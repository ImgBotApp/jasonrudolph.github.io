---
title: "Programming Groovy: Metaprogramming no longer an afterthought"
layout: post
tags:
- book
- groovy
---
I recently finished a tech review of [Venkat Subramaniam's](http://agiledeveloper.com/blog/ "Agile Developer - Venkat Subramaniam's Blog") upcoming book from the Pragmatic Programmers, [*Programming Groovy: Dynamic Productivity for the Java Developer*](http://pragprog.com/titles/vslg "The Pragmatic Bookshelf — Programming Groovy"), and I was pleased to find that Venkat included a healthy dose of "[the red pill](http://groovygrails.com/gg/conference/speaker?speakerId=18&amp;showId=131#pr8897 "Scott Davis at 2GX - Groovy, The Red Pill: Metaprogramming, the Groovy Way to Blow a Buttoned-Down Java Developer's Mind")."         

![2008-01-20 Programming Groovy Cover](/resources/20080120-programming-groovy-cover.jpg)

Scott Davis's [red pill/blue pill](http://groovygrails.com/gg/conference/speaker?speakerId=18&amp;showId=131#pr8896 "Scott Davis at 2GX - Groovy, the Blue Pill: Writing Next Generation Java Code in Groovy") metaphor is spot on ...  

> You take the blue pill, the story ends, you wake in your bed and you believe whatever you want to believe.

Many developers (and almost all Groovy tutorials and books to date) are still focused on the more conservative features of the Groovy language.  Admittedly, the [conveniences](http://groovy.codehaus.org/Closures "Groovy - Closures") [offered](http://groovy.codehaus.org/Collections "Groovy - Collections") [by](http://groovy.codehaus.org/Database+features "Groovy - Database features") [that](http://groovy.codehaus.org/Processing+XML "Groovy - Processing XML") [slice](http://groovy.codehaus.org/Testing+Guide "Groovy - Testing Guide") [of](http://groovy.codehaus.org/Regular+Expressions "Groovy - Regular Expressions") [Groovy](http://groovy.codehaus.org/groovy-jdk/ "Groovy JDK") are nothing to scoff at, but it's frankly short-sighted to stop there.  After all, it's metaprogramming (i.e., the red pill) that gets the credit for much of the [coolness that one experiences in a Grails app](http://grails.org/Dynamic+Methods+Reference "Grails - Dynamic Methods").  And without metaprogramming, Groovy wouldn't have a chance in the [DSL](http://docs.codehaus.org/display/GROOVY/Writing+Domain-Specific+Languages "Groovy - Writing Domain-Specific Languages") world.  

Venkat clearly wasn't content to let Groovy metaprogramming continue to take a back seat.  Instead, he's dedicated four whole chapters to this important topic.  By page count, that's more than 20% of the book!  And that's not even counting the numerous cameos that metaprogramming makes in other chapters, especially in the discussions on testing and DSLs.  Want to know when to use `#invokeMethod` versus `#methodMissing`?  Venkat's got you covered.  Need to get your head around categories, expandos, and the `ExpandoMetaClass`? You're all set. Not sure how to differentiate between method injection and method synthesis?  Not for long.  

The [beta book is available now](http://pragprog.com/titles/vslg "The Pragmatic Bookshelf — Programming Groovy").  Of course, it's *beta*, so you'll have to be forgiving of the areas that still need some polish.  But whether you check out the book now, or you wait for it to graduate from beta status, the red pill awaits.  Bottom line: You simply won't find a more comprehensive resource for getting up to speed on Groovy metaprogramming.
