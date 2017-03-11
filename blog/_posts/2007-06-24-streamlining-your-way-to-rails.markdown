---
title: Streamlining your way to Rails
layout: post
tags:
- grails
- rails
- ruby
- streamlined
---
By the time you've knocked out your first few [Rails](http://rubyonrails.org) apps, you're probably not particularly excited about starting another UI from scratch.  You're still jazzed about the fact that ActiveRecord is going to save you from all the boilerplate ORM plumbing, and you're psyched to be developing in a dynamic (and elegant and powerful) language like Ruby, but it's hard to actually look forward to manually wiring up the relationships in the UI (again), tediously tying in Ajax in all the usual places (again), implementing live search (again), adding in pagination and sortable lists (again), and, well, you get the idea.  Developing in Rails is supposed to be *enjoyable*, so we need something to bring the overall pleasantness of Rails into *these* areas of application development as well.

Enter [Streamlined](http://www.streamlinedframework.org/)...


<!--more-->

![2007-06-23 Streamlined Logo](/resources/20070623-streamlined-logo.png)

...and enable *all* of those features and more with just a small helping of declarative decoration.  

If a picture's worth a thousand words...

![2007-06-23 Streamlined Screenshot](/resources/20070623-streamlined-screenshot.png)

...a [screencast](http://www.streamlinedframework.org/pages/screencasts) is easily worth some vast multiple of that.  The application shown above is the result of a whopping 5 minutes of effort, and you can see [Justin Gehtland](http://www.relevancellc.com/about) develop it even more fully (in a nice iterative fashion) over the course of three [screencasts](http://www.streamlinedframework.org/pages/screencasts).  And once you've seen it in action, surely you'll be ready to try it out first-hand. Check out [Matthew Bass's recent tutorial](http://matthewbass.com/2007/05/28/getting-started-with-streamlined-part-1), and you'll have your own Streamlined app up and running in just a few short steps.

Just like Rails itself, Streamlined was initially extracted from real world projects.  [Relevance](http://relevancellc.com) contributed the initial 0.0.1 release (open source under the MIT license) to the community approximately a year ago, and now the 1.0 release is right around the corner.  The Streamlined team has recently added several new committers (myself included) to help with the push forward.  

It's nearing feature-complete status, and the emphasis is now shifting toward code coverage and documentation.  Last week, [Stuart Halloway](http://www.relevancellc.com/about) and I spent a day pair programming our way through some of the elusive corners of the code that were lacking proper test coverage.  We managed to make a decent dent, and Streamlined is well on its way to 100% C0 code coverage.  

Stay tuned for 1.0!

--

As an aside, in the [Grails](http://grails.org) world, similar features have started to appear both in [Siegfried Puchbauer's ext plugin](http://dev.puchbauer.com/extui/extUi) and in [Daiji Takamori's ScaffoldTags plugin](http://snowmochi.com/grails/scaffoldTags/).  Expect these exciting plugins to continue to grow and support this rich, eye-popping functionality.
