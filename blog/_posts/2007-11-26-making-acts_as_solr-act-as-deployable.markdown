---
title: Making acts_as_solr act as deployable
layout: post
tags:
- rails
- ruby
---
[We](http://thinkrelevance.com "Relevance, Inc.") recently deployed two new [Solr](http://lucene.apache.org/solr/ "Apache Solr")-powered apps, and thanks to [acts\_as\_solr](http://acts-as-solr.railsfreaks.com/acts_as_solr "acts_as_solr Rails plugin"), *most* of the task of integrating Solr with Rails was downright trivial.  Deployment, however, came with a few small roadbumps.

![Solr](/resources/20071127-solr.png)

## Know when to nohup

When using acts\_as\_solr locally, you start and stop Solr via the provided rake tasks (i.e., `rake solr:start` and `rake solr:stop`).  However, when you run the `solr:start` task, you'll quickly notice that all of the would-be log output is right there in your face, and definitely *not* in some well-tucked-away log file.  During development, we didn't think too much of it.  Just open a new terminal tab, start Solr, and get back to devving.

But then came time for deployment.  Try to run the vanilla `solr:start` task as part of a Capistrano deployment, and you'll quickly be looking for another option.  As you watch your deploy script run, here comes all that same output you've been seeing locally ... but when Cap completes, Solr calls it quits.  We need a way to tell Solr to keep running in the background, even after Cap finishes doing its thing.  

<pre lang="ruby">nohup rake solr:start > #{shared_path}/log/solr.log 2> #{shared_path}/log/solr.err.log</pre>

(Incidentally, you may want to employ this solution for your local Solr instance as well.  After all, that'll be one fewer terminal window cluttering your workspace.)

## Dude, where's my index?

Now that you have a reliable means for starting and stopping Solr, it's time to decide where you want to store your index files.  By default, acts\_as\_solr defines `SOLR_PATH` as `#{RAILS_ROOT}/vendor/plugins/acts_as_solr/solr`, which means that Solr will store your index files in `#{RAILS_ROOT}/vendor/plugins/acts_as_solr/solr/#{RAILS_ENV}/solr/data/#{RAILS_ENV}/index`.  If you keep that setup, what happens when you deploy a new release of your app?  You guessed it: your index files get left behind with the old release.  

But that's almost certainly not the behavior you want.  The index files represent data, not application code.  You don't move your database every time you deploy a new release, and you shouldn't move - or even worse, recreate - your Solr indexes with every release either.  (Yes.  Just as some releases require database changes, so will some releases require reindexing.  But, it's definitely not a need for *every* release, and it therefore shouldn't be your normal practice.)

At this point, you have a few choices, but the goal with each choice remains the same: find a home for the Solr indexes to allow them to survive across multiple deployments.  First, copy `#{RAILS_ROOT}/vendor/plugins/acts_as_solr/solr` to a release-independent location in your deployment environment.  Then, you just need to tell your application where to find that directory.  Ultimately, `SOLR_PATH` needs to point to that location.  If you don't want to change the default acts\_as\_solr settings, then you can configure your deployment script to symlink the copied directory into the location where acts\_as\_solr expects to find it (i.e., `#{RAILS_ROOT}/vendor/plugins/acts_as_solr/solr`).  Otherwise, you can simply change the definition of `SOLR_PATH` (defined in `#{RAILS_ROOT}/vendor/plugins/acts_as_solr/config/environment.rb`) to point to your release-independent directory.

## Know your role

Now you have a home for our Solr indexes and you have an easy way to start and stop Solr via Capistrano, but where exactly should Solr itself run?  We all want highly performant apps, so you may be tempted to consider running Solr on multiple servers.  More is always better.  Right?  

STOP!  

Your app communicates with Solr via HTTP, so Solr can live anywhere on your network.  It doesn't need to live on the same box as your app, as your database, etc.  And while you technically *could* run Solr on all your app servers, it's highly unlikely that you'll want to do so.  Think about the problems associated with managing redundant *databases*.  Do you really want to manage multiple sets of Solr indexes and try to make sure they all have the same data?  Unless you're Google - in which case, this stuff is your bread and butter - of course not.  

If you store the indexes in a shared location and have all the Solr servers use the same indexes, does that make things any easier?  Well, you no longer have to keep multiple indexes in sync, but you now have a different problem: data corruption.  <del>Solr isn't designed to share indexes among multiple Solr processes, and when two processes try to update the same indexes, you're in for all kinds of trouble.</del>  **UPDATE**: Solr isn't designed to have multiple Solr processes updating a shared set of indexes.  (As a reader pointed out to me, Solr *is* capable of supporting a [distributed installation](http://wiki.apache.org/solr/CollectionDistribution), but all *changes* are routed to a single master Solr instance, and multiple query slaves receive the updates from the master.)

So let's steer clear of all that trouble and find an easy way to run Solr on a single server, while having all your app servers talk to that Solr instance.  First up, define a distinct role for the server where you want Solr to run.

<pre lang="ruby">task :production do
  role :web, 'app.example.com'
  role :app, 'app.example.com'
  role :solr, 'solr.example.com'
  role :db, 'db.example.com'
end
</pre>

Next, simply define the tasks needed to start and stop Solr on that server, and you're good to go.  (Also notice that we include a task to symlink in the Solr indexes from the release-independent directory discussed above.)  

<pre lang="ruby">before "deploy:update_code", "solr:stop"
after "deploy:symlink", "solr:symlink"
after "solr:symlink", "solr:start"

namespace :solr do
  desc "Link in solr directory"
  task :symlink, :roles => :solr do
    run <<-CMD
      cd #{release_path} &&
      ln -nfs #{shared_path}/solr #{release_path}/solr
    CMD
  end

  desc "Before update_code you want to stop SOLR in a specific environment"
  task :stop, :roles => :solr do
    run <<-CMD
      cd #{current_path} &&
      rake solr:stop RAILS_ENV=#{env}
    CMD
  end

  desc "After update_code you want to restart SOLR in a specific environment"
  task :start, :roles => :solr do
    run <<-CMD
      cd #{current_path} &&
      nohup rake solr:start RAILS_ENV=#{env} > #{shared_path}/log/solr.log 2> #{shared_path}/log/solr.err.log
    CMD
  end
end
</pre>

And with that little bit of setup, you're ready to rock!  (Well, er, as much as one can *rock* to full-text search.)    

--

If you want full-text search in your Rails app, definitely take acts\_as\_solr for a spin.  You'll be up and running in no time, and chances are your users will love the new dimension that full-text search brings to your application.        

## Looking ahead
As for us, now that these apps are live and flexing all their Solr might, we're on to looking for ways to make them better, faster, stronger.  Long term, we definitely don't want to maintain the default behavior of synchronously waiting for acts\_as\_solr to make the call to Solr (in order to update the indexes) each time we save a Solr-enabled ActiveRecord model object.  In our apps, it's more important that we quickly save the object and provide a prompt response back to the user.  If it then takes a few seconds of background processing before that change is reflected in Solr, that's perfectly acceptable (and much preferred over causing the user to wait for us to update the Solr indexes).  At least [one open source project](http://background-solr.rubyforge.org/svn/README "acts_as_background_solr Rails plugin") is already dedicated to mitigating this issue, and we hope to explore this and various asynchronous solutions in the near future.
