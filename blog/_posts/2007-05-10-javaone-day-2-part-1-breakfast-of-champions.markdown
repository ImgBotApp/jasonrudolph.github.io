---
title: "JavaOne Day 2, Part 1: Breakfast of champions"
layout: post
tags:
- grails
- java
---
Day 2 was a marathon for sure, but it was well worth it.  Time for the morning report...

### Creating Amazing Web Interfaces with Ajax
Presented by Ben Galbraith and Dion Almaer (Co-authors of [Pragmatic Ajax](http://www.pragmaticprogrammer.com/titles/ajax/?ajaxian) and Founders of [Ajaxian.com](http://ajaxian.com))

It's been two years now since I first saw Ben Galbraith's and Stu Halloway's rockstar presentation on Ajax at NFJS, and I was pleased to see another great talk today showing just how very far things have progressed in that time.  The plumbing continues to fade into the background, allowing devs to focus more and more on the problem domain and less on the details of HTTP status codes, etc.


<!--more-->

It looks like we can expect [Ext JS](http://extjs.com/) to introduce yet one more layer of abstraction, as it's providing some great looking widgets built on top of Yahoo! UI, jQuery, Protoype, and Dojo.  (If you'd like to see a quick example of what Ext JS can do to [Grails](http://www.grails.org/scaffolding) scaffolding, be sure to check out [Siegfried Puchbauer's recent proof-of-concept](http://dev.puchbauer.com/extdemo/extBook) app.)

`<sidebar>`Offline apps are getting a lot of attention these days, especially considering the built-in support that's [coming in Firefox v3](http://www.readwriteweb.com/archives/firefox_3_offline_apps.php).  Personally, I predict that we as an industry will go too far here.  We'll try to add offline capabilities to things that just don't make any sense to be offline, and then of course, the pendulum will swing back the other way.  While offline apps bring a lot of advantages with them, there's still a fundamental stumbling block to overcome: syncing is hard.  And it's doubly hard to reliably sync in a way that the average user will always find intuitive.  If we knew for sure that ubiquitous connectivity was two years away, I'd say there's no value in pursing offline apps at all.  But if ubiquitous connectivity ends up eluding us for another decade, well, maybe it's time to start throwing some more Ph.D.s at the syncing challenge and welcome offline apps to the fold.`</sidebar>`

Ben and Dion talked about the future state for Ajax, most interestingly concerning the faster JS interpreters we should see in the near future and the significant changes coming in the HTML v5 spec.  Ben pointed out that we haven't yet seen a good solution for adding sound effects to web apps and referred to sound as the "last frontier."  (Frankly, I'd be quite satisfied if that's a frontier we never cross.  Web sites that play sound are evil...unless I specifically *ask* for sound, à la streaming music for example.)

All in all, it was a good session with well-chosen demoes from two people that know this space inside and out.

### Effective Java Reloaded: This Time It's for Real
Presented by Josh Bloch (Chief Java Architect at Google and Author of [Effective Java](http://java.sun.com/docs/books/effective/))

The first edition of [Effective Java](http://java.sun.com/docs/books/effective/) rightfully earned its place as required reading for any serious Java developer, and with the significant changes to the Java language since that edition was published, many developers have been begging for a revision.  In this session, Josh Bloch delivered a promising preview of the updates that are in the pipeline.

The majority of Josh's tips focused on the proper use of generics, and rightfully so, as they clearly represent the most significant of all the language changes in Java 5.  And while the information on generics was certainly handy, I particularly enjoyed Josh's continued emphasis on the benefits of immutability.  As one of my favorite themes in the first edition, I'm glad to see it's back with a vengeance in the upcoming revision.  

It sounds like Josh had hoped to have the second edition out in time for JavaOne this year, but he promises it will be here before JavaOne '08.  Until then, we'll have to rely on the slides (which luckily should be landing on [sun.com](http://developers.sun.com/learning/javaoneonline/j1sessn.jsp?sessn=TS-2689&yr=2007&track=5) within the next day or so).

--

Stay tuned for the afternoon report.
