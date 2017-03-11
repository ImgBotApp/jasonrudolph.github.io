---
title: "Git init: Say hello to agility"
layout: post
tags:
- agile
- git
---
With all the recent fuss about the [game-changing advantages of Git](http://git.or.cz/#about "Git - Fast Version Control System") and distributed version control in general, it would be easy to overlook what Git does for deciding *whether* (and when) to use version control for a given task.  Sure, Git makes non-linear development a breeze, it manages large projects with uncanny efficiency, and we probably can't even fathom yet just how transforming [github](http://github.com/ "Secure Git hosting and collaborative development - GitHub") is going to be for open source.  But, if you look closely, there's something worth noting way before you create your first branch, before your project is even thirty minutes old, and well before you're ready to share it with the community:  git init is so pleasantly simple, you'll never again think twice about "whether it's worth it" to throw something into version control.

As someone who had the, um, "joy," of working with CVS, SourceSafe, ClearCase, and other SCM "solutions" that made you wish you were instead [just using NTFS](http://railsenvy.com/2008/4/16/rails-envy-podcast-episode-027-04-16-2008#comment-1304 "Rails Envy Podcast - Episode #027: 04/16/2008 - NTFS equals 'no version control at all'"), I definitely appreciate what SVN did for the state of version control systems.  Nevertheless, there were countless prototypes, drafts, experiments, etc. that I talked myself out of storing in SVN. The conversation typically went something like so:  "Do I really want to create a new repository just for this experiment?  Should it go in my local repo, or does it belong up on the shared repo?  Should I bother setting up the standard dirs for trunk, tags, and branches?  Maybe I should just add it to a grab-bag repo for now?  Nah.  Forget it.  It's not worth the trouble *yet*."  

Git removes many of those decisions altogether, and (in true agile fashion) it allows me to defer the others until they actually matter.  I can ["execute, build momentum, and move on."](http://gettingreal.37signals.com/ch06_Done.php "Getting Real: "Done!" (by 37signals)")  Let's say I'm halfway through a blog post, and I decide that I want to try taking it in a different direction.  No problem.  Drop it in Git, and experiment away...

<pre lang="text">
BlogPosts> ls
20080422_git_is_agile.blog.md
BlogPosts> git init
Initialized empty Git repository in .git/
BlogPosts> git add .
BlogPosts> git commit -m "i can haz repo?"
Created initial commit 417554e: i can haz repo?
 1 files changed, 25 insertions(+), 0 deletions(-)
 create mode 100644 20080422_git_is_agile.blog.md
</pre>

So while you'll continue to hear people (myself included) champion Git's importance as a solution for *team*-based or *community*-based development, its ability to give you *instant*, no-questions-asked version control is enough to earn a place for Git on your system, **even if you're the only one who will ever see your work**.

And Git's agility doesn't stop there.  From [branching on a dime](http://www.kernel.org/pub/software/scm/git/docs/user-manual.html#managing-branches "Git User's Manual (for version 1.5.3 or newer) - Managing Branches"), to the oh-so-beautiful [stash](http://www.kernel.org/pub/software/scm/git/docs/git-stash.html "git-stash"), to the [ability to rework past commits](http://blog.madism.org/index.php/2007/09/09/138-git-awsome-ness-git-rebase-interactive "git awsome-ness [git rebase --interactive] - MadBlog"), Git reminds me that decisions are temporary.  Or, to quote Ryan Tomayko, ["Git means never having to say, 'you should have.'"](http://tomayko.com/writings/the-thing-about-git "The Thing About Git")

--

Be sure to check out [Rob's post](http://robsanheim.com/2008/02/22/learn-git-10-different-ways/ "Panasonic Youth - Learn Git 10 Different Ways") for a whole host of Git-infused goodness.
