---
title: Groovy 1.1-beta-2 released, introduces joint compiler for Java & Groovy!
layout: post
tags:
- groovy
- java
---
In one fell swoop, the Groovy team and JetBrains have seemingly annihilated the biggest reason (and perhaps the only reason) *not* to use Groovy in your Java project.  With today's release of Groovy 1.1-beta-2, you can now use the groovyc compiler to jointly compile both your Groovy and Java classes.  And here's the kicker: it manages all the dependencies for you!  Groovy class A extends Java class B which references Groovy class C?  No problem.


<!--more-->

![2007-07-05 Groovy Duke](/resources/20070705-groovy-duke.jpg)

In my review of [Groovy in Action](http://jasonrudolph.com/blog/2007/06/13/infoq-review-groovy-in-action/), I cited this "chicken and egg dependency problem" and its potential workarounds as the one area of the book that I thought could have been stronger.  This topic is just so incredibly important.  Once you're able to use Groovy and Java in the same project with zero concern about whether your build script can work out the dependencies, you're suddenly free to explore Groovy to the fullest extent, to drop it in wherever Java feels the least bit cumbersome.  Doing file I/O and don't want the hassle of the all the plumbing needed to manage file handles and make sure you clean them up properly?  No worries.  Just use [Groovy](http://groovy.codehaus.org/groovy-jdk.html#cls13).  Need to parse XML and cringe at the thought of walking a DOM tree or setting up a SAX parser?  Problem solved.  Just use [Groovy](http://groovy.codehaus.org/Reading+XML+using+Groovy's+XmlSlurper).  Need closures and don't want to wait until Java 7?  Ha!  Java has closures *today*!  Just use [Groovy](http://groovy.codehaus.org/Closures).

Jochen Theodorou offers a [detailed write-up](http://blackdragsview.blogspot.com/2007/07/joint-compilation-in-groovy.html) of how he and Alex Tkachman ([JetBrains](http://www.jetbrains.net/confluence/display/GRVY/Groovy+Home)) worked together to develop a clever solution to this previously tedious problem.  Well done, Guys.  Well done.  

And this feature is just one of several new improvements available in this release.  (If you're one of the many folks longing for Groovy to support the classic `for` loop, good news: the wait is over.  But honestly, you really should give the [Groovier solution](http://groovy.codehaus.org/Looping#Looping-forloop) a chance.)  Be sure to check out [Guillaume Laforge's post](http://glaforge.free.fr/weblog/?itemid=219) for full details on this important milestone on the road to Groovy 1.1.
