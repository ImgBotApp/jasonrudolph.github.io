---
title: Grails 0.6 released, brings new flow to Grails development
layout: post
tags:
- grails
- groovy
---
Grails 0.6 is in the wild, and watch out...your Grails development is about to get a serious shot in the arm!

![Grails Logo](/resources/20070903-grails-logo.jpg)

Without a doubt, the developer experience was one of the key motivating factors in my original journey to Grails (and away from some Java web frameworks that shall remain nameless).  And somewhat unfortunately, while the [last](http://jasonrudolph.com/blog/2007/01/31/grails-04-hits-the-street/ "Grails 0.4 Hits the Street") [few](http://jasonrudolph.com/blog/2007/05/01/grails-05-shipped-the-cup-overfloweth/ "Grails 0.5 Shipped: The Cup Overfloweth!") releases have been packed with new features and increased modularity, each release has brought with it slower start-up times, more time needed to run tests, etc.  As a framework still on it's way to 1.0, that's probably acceptable, and perhaps even expected, as performance optimizations had not yet been a priority.  But as someone that greatly values the developer experience, and as someone that [regularly stands in front of a room full of developers](http://www.nofluffjuststuff.com/ "No Fluff Just Stuff") while waiting for a demo app to start, the speed bumps in 0.6 are a welcome improvement.    

And these speed increases are no small enhancement. We're talking about *at least* a 50% reduction in start-up times. The next time you run `grails run-app` or `grails shell`, you're bound to think it was preceded by a stealth installation of some crazy new plugin.  ;-)

<span style="font-family: monospace">grails install-plugin [powerthirst](http://www.youtube.com/watch?v=qRuNxHqwazs "YouTube - Powerthirst")</span> (NSFW)

In fact, these speed bumps make experimentation the most viable it's ever been with Grails.  Wanna try something out before adding it to your service class?  No problem.  Just run `grails shell` and you've got a fully-bootstrapped Grails environment with complete access to all your domain classes, service classes, etc.

And as someone who thinks [you can never have too may tests](http://thinkrelevance.com/relevance-development "Relevance - How We Develop Software"), the fact that your unit and integration tests now run faster is a big boost as well.

Of course, improved developer productivity isn't the only thing that's noteworthy in this release.  There are several new features to try out as well.  Some of the heavy hitters include

* [Joint Groovy/Java compilation](http://jasonrudolph.com/blog/2007/07/05/groovy-11-beta-2-released-introduces-joint-compiler-for-java-groovy/ "Groovy 1.1-beta-2 Released, Introduces Joint Compiler for Java &#038; Groovy!")
* [Improved support for REST](http://grails.org/0.6+Release+Notes#0.6ReleaseNotes-RESTandXMLWebServices) with automatic XML/JSON marshaling and RESTful URL mappings
* [New configuration DSL](http://grails.org/0.6+Release+Notes#0.6ReleaseNotes-UnifiedCentralizedConfigurationDSL) for those times when you want to step outside the bounds of *convention over configuration*

And not only does development itself have a newfound *flow* to it (thanks to the speed increases discussed above), this release also introduces a DSL for defining web flows and managing conversational state in your application.  This DSL greatly simplifies much of the logic traditionally crammed into controllers, and instead expresses the behavior in a much more natural and readable manner.  Be sure to check out [Graeme's example](http://graemerocher.blogspot.com/2007/08/grails-06-released-with-rich.html "Graeme Rocher's Blog: Grails 0.6 Released with Rich Conversation Support (AKA Spring Web Flow)") to get a feel for what's possible with this new and rich means for expressing the flow of your web application.

It's worth having a look at the [release notes](http://grails.org/0.6+Release+Notes "Grails - 0.6 Release Notes") for full details on the many improvements in this release, complete with code samples and screen shots.  

This marks [the last big release prior to Grails 1.0](http://grails.org/roadmap "Grails - Roadmap"), so [grab it](http://grails.org/Download "Grails - Download") while it's hot, and have fun!

----------------

Resources

* [Read the Grails 0.6 Release Notes](http://grails.org/0.6+Release+Notes "Grails - 0.6 Release Notes")
* [Download Grails 0.6](http://grails.org/Download "Grails - Download")
