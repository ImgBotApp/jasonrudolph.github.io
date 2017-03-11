---
title: "JavaOne Day 2, Part 3: Solutions for sanity"
layout: post
tags:
- grails
- java
---
Day 2 wrapped up with talks on ways to stay sane when developing in two particular problem domains: concurrency and web apps.  And since those domains certainly aren't mutually exclusive, this pair of sessions made for a good closing to a solid day of Java geekery.

### Effective Concurrency for the Java Platform
Presented by [Brian Goetz](http://www.briangoetz.com/) (Author of [Java Concurrency in Practice](http://www.amazon.com/gp/product/0321349601))

Much like Josh Bloch and Bill Pugh did on [Day 1](http://jasonrudolph.com/blog/2007/05/09/javaone-day-1-javautilrandom-observations/), Brian Goetz demonstrated his uncanny knack for taking a complex problem space and presenting it in a manner that's both easily digestible and fun to learn.


<!--more-->

I found the overall theme of the presentation especially refreshing:  It's not the nuances of semaphores and mutexes that power successful concurrent programming; it's a foundation of sound software engineering practices (i.e., the practices we should all be using with or without concurrency) that constitute the recipe for success.  If you skimp on documentation, pay insufficient attention to encapsulation, or fail to clearly communicate the intent behind your code, you're in for trouble...and even more so when dealing with concurrency.  

Along those same lines, Brian argued that the ease of reading code is even more important than the ease of writing it.  In other words, if you don't write code a maintainer can understand, don't expect him to do the right thing when he changes your code.  I wholeheartedly agree.  The solution: write code that you're proud of, code you'd gladly show to others.  

To help developers more clearly communicate the intent behind their code, Bill Pugh, Brian Goetz, and others have proposed several new annotations in [JSR 305](http://jcp.org/en/jsr/detail?id=305).  And, of course, once we have those annotations in place, that opens the door for tools like FindBugs to validate that the code actually complies with its stated intent.  Nice!

And as if [Josh Bloch's arguments for immutability](http://jasonrudolph.com/blog/2007/05/10/javaone-day-2-part-1-breakfast-of-champions/) earlier in the day weren't enough, Brian encouraged developers to "prefer immutable objects," especially when working in a concurrent environment.  After all, if you're immutable, you're automatically thread-safe.  What's not to like?

### Grails: Spring + Hibernate Development Reinvented
Presented by [Graeme Rocher](http://graemerocher.blogspot.com/) ([Grails](http://grails.org) Project Lead and Author of [The Definitive Guide to Grails](http://www.apress.com/book/bookDisplay.html?bID=10205))

After a [long](http://jasonrudolph.com/blog/2007/05/10/javaone-day-2-part-1-breakfast-of-champions/) [day](http://jasonrudolph.com/blog/2007/05/10/javaone-day-2-part-2-an-afternoon-of-rich-uis/) of geeking out, by 10 PM, I was wiped out.  Nevertheless, I was pumped to see Graeme show off Grails to the JavaOne crowd.  For folks that weren't familiar with Groovy, he spent a few minutes explaining the benefits of Groovy, its seamless integration with Java, and its high approachability for Java developers.  To demonstrate that approachability, Graeme first showed some Java code that was roughly equivalent to something like this:

    // A Java Class
    public class Circle {
        private int radius;

        public Circle(int radius) {
            this.radius = radius;
        }

        public int getDiameter() {
            return radius * 2;
        }
    }

And he then showed the equivalent class in Groovy:

    // A Groovy Class
    public class Circle {
        private int radius;

        public Circle(int radius) {
            this.radius = radius;
        }

        public int getDiameter() {
            return radius * 2;
        }
    }

How's that for a learning curve?!  Of course, an idiomatic Groovy class wouldn't be that verbose, but the point was well taken nonetheless.  

He then offered up the idiomatic Groovy version of the same class:

    // An Idiomatic Groovy Class
    class Circle {
        def radius

        def getDiameter() {
            radius * 2
        }
    }

After then discussing the Grails basics, Graeme later demonstrated a handful of power features.  The audience got to see first hand just how easy it is to add Spring remoting to a Grails app, to intermingle both Grails and Java domain classes in a single app, or to return to the familiarity of Hibernate and Spring configuration if/when the need arises in your Grails app.

--

And with that, Day 2 is in the can.  Day 3's report is right around the corner.
