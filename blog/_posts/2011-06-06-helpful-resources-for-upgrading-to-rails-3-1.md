---
title: "Helpful resources for upgrading to Rails 3.1"
layout: post
tags:
- rails
---

The first [Rails 3.1 release candidate](http://weblog.rubyonrails.org/2011/5/22/rails-3-1-release-candidate "Riding Rails: Rails 3.1: Release candidate") has been out for a couple weeks now, and the official release of 3.1.0 can't be far behind.  

## Upgrading to Rails 3.1

I upgraded a Rails 3.0 app to 3.1 this past weekend, and all in all, it was a pretty smooth process.  Along the way, I was grateful to discover a few helpful posts from developers that had already made this journey.  If you're getting ready to upgrade an existing app to Rails 3.1, or if you just want to get a feel for what to expect, I recommend checking out these write-ups.

* [Read This Before Installing Rails 3.1 (Daniel Kehoe)](http://railsapps.github.com/installing-rails-3-1.html "Read This Before Installing Rails 3.1")
* [How to Upgrade to Rails 3.1.0 (David Rice)](http://davidjrice.co.uk/2011/05/25/how-to-upgrade-a-rails-application-to-version-3-1-0.html "David Rice - How to Upgrade to Rails 3.1.0")
* [Migrating My Blog over to Rails 3.1 Beta (Fabio Akita)](http://www.akitaonrails.com/2011/05/31/migrating-my-blog-over-to-rails-3-1-beta "Migrating my blog over to Rails 3.1 beta - AkitaOnRails.com")
* [Deploying a Rails 3.1 Application to Production (Richard Taylor)](https://moocode.com/posts/1-deploying-a-rails-3-1-application-to-production)
* [Upgrading to Rails 3.1 (RailsCasts)](http://railscasts.com/episodes/282-upgrading-to-rails-3-1 "RailsCasts - #282 Upgrading to Rails 3.1")

## More Rails 3.1 resources

If you're already up to speed on all the new features in Rails 3.1, then you're ready to give the upgrade a shot.

Still here?  Well, I'm guessing that means you want to spend a bit more time wrapping your head around what's new in Rails 3.1, and *then* you'll be ready for the upgrade.  Good news: you've got quite a few resources to lean on:

### The big picture

* [Rails 3.1 Release Notes (RailsGuides)](http://guides.rubyonrails.org/3_1_release_notes.html "Ruby on Rails Guides: Ruby on Rails 3.1 Release Notes")
* [Rails 3.1 Announcement and Overview (Aaron Patterson)](http://weblog.rubyonrails.org/2011/8/31/rails-3-1-0-has-been-released "Riding Rails: Rails 3.1.0 has been released!")
* [Rails 3.1 Overview (RailsCasts)](http://railscasts.com/episodes/265-rails-3-1-overview "RailsCasts - #265 Rails 3.1 Overview")
* [Changelog between 3.0 and 3.1 (Ryan Bates)](https://gist.github.com/958283 "Gist (from Ryan Bates) cataloging the changes between Rails 3.0 and Rails 3.1 beta")

### Individual features

* Asset Pipeline
  * [Asset Pipeline Documentation (RailsGuides)](http://guides.rubyonrails.org/asset_pipeline.html "Ruby on Rails Guides: Asset Pipeline")
  * [The Asset Pipeline and Our Post-Modern, Hybrid, Javascript Future (DHH's Keynote at RailsConf 2011)](http://www.youtube.com/watch?v=cGdCI2HhfAU "RailsConf 2011, David Heinemeier Hansson Keynote - The Asset Pipeline and Our Post-Modern, Hybrid, Javascript Future")
  * [Understanding the Asset Pipeline (RailsCasts)](http://railscasts.com/episodes/279-understanding-the-asset-pipeline "RailsCasts - #279 Understanding the Asset Pipeline")
* HTTP Streaming
  * [Why HTTP Streaming? (Xavier Noria)](http://weblog.rubyonrails.org/2011/4/18/why-http-streaming "Riding Rails: Why HTTP Streaming?")
  * [HTTP Streaming (RailsCasts)](http://railscasts.com/episodes/266-http-streaming "RailsCasts - #266 HTTP Streaming")
* CoffeeScript
  * [CoffeeScript Basics (RailsCasts)](http://railscasts.com/episodes/267-coffeescript-basics "RailsCasts - #267 CoffeeScript Basics")
  * [Official CoffeeScript Documentation (coffeescript.org)](http://coffeescript.org "CoffeeScript")
* Sass
  * [Sass Basics (RailsCasts)](http://railscasts.com/episodes/268-sass-basics "RailsCasts - #268 Sass Basics")
  * [Official Sass Documentation (sass-lang.com)](http://sass-lang.com/ "Sass - Syntactically Awesome Stylesheets")
* [Reversible Migrations (Rohit Arondekar)](http://edgerails.info/articles/what-s-new-in-edge-rails/2011/05/06/reversible-migrations/index.html "Edge Rails.info :: Reversible Migrations")
* [jQuery as the New Default JavaScript Library (Xavier Noria)](http://weblog.rubyonrails.org/2011/4/21/jquery-new-default "Riding Rails: jQuery: New Default")
* [ActiveRecord Identity Map (Josh Kalderimis)](http://edgerails.info/articles/what-s-new-in-edge-rails/2011/04/21/activerecord-identity-map/index.html "Edge Rails.info :: ActiveRecord Identity Map")

## Party on, dudes

If Rails 3.1 has piqued your curiosity, it's definitely worth a quick spike to try out an upgrade.  Just create a branch and give it a shot.  After all, you wrote all those tests for a reason, right?  Take Rails 3.1 for a spin, and let your test suite tell you where things need to be patched up.  What have you got to lose?  [Party on, Dudes!](http://www.youtube.com/watch?v=WVXGC896Jdw "YouTube - Bill and Ted's Excellent Adventure - The Future Council")

--

**Updated 8/27/2011** - Added links to the asset pipeline docs from Ryan Biggs and the new RailsCasts episode on "Understanding the Asset Pipeline."

**Updated 9/6/2011** - Added link to the new RailsCasts episode on "Upgrading to Rails 3.1."  Added link to the official Rails 3.1.0 release announcement and release notes.
