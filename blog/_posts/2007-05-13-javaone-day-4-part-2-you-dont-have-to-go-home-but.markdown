---
title: "JavaOne Day 4, Part 2: You don't have to go home, but..."
layout: post
tags:
- java
- ruby
- scala
---
Well folks, the tenth and final installment is upon us.  Just three more sessions make up our home stretch...

### The Scala Experience -- Safe Programming Can Be Fun!
Presented by [Martin Odersky](http://lamp.epfl.ch/~odersky/) (Professor in the [School of Computer and Communication Sciences](http://ic.epfl.ch/) at [EPFL](http://www.epfl.ch/))

The [Java Posse](http://javaposse.com/) has been [chatting](http://javaposse.com/index.php?post_id=199323) [up](http://javaposse.com/index.php?post_id=197338) [Scala](http://scala-lang.org) for some time now, so what better way to see what all the fuss is about than to get the scoop on Scala straight from its designer?

Martin describes Scala as a *union* of functional and OO programming.  This statically-typed language is purely object-oriented and completely interoperable with Java.  Martin demonstrated the immense flexibility of Scala and explained how Scala achieves that flexibility via its emphasis on the use of library abstractions (as opposed to rigid language syntax) to express problems and their solutions.  

It was cool to see that Martin wasn't afraid to get down and dirty with some good deep Computer Science topics.  Over the course of about 10 minutes, he explained step-by-step how the compiler works to translate from the programmer's initial Scala source code to an expanded (more verbose) source code and then all the way down to Java bytecode.  (Ah.  [CS 571](http://etg08.itc.virginia.edu/cod/servlet/CourseInfo?term=20043&mnemonic=CS&course_nbr=571).  Those were the good ol' days.).  And once compiled, it turns out that Scala's average execution time is not only comparable with Java, it actually *outperforms* Java in in certain (highly parallel) tests.

[![Scala/Java Comparison](/resources/20070513-scala-java-comparison-tn.png)](/resources/20070513-scala-java-comparison.png) [![Scala Summary](/resources/20070513-scala-summary-tn.png)](/resources/20070513-scala-summary.png)

### Declarative Programming: Tighten Enterprise JavaBeans (EJB) 3.0 and JSR 303 Beans Validation
Presented by Emmanuel Bernard* (Core Developer at [JBoss](http://jboss.com/) and Lead Developer of [Hibernate Annotations](http://annotations.hibernate.org/) and [Hibernate Validator](http://validator.hibernate.org))

Those Hibernate guys clearly aren't ones to sit around and idly enjoy past successes.  Nope.  If there's any pain point lingering in or around Java ORM, you can count on them to take it on.  This time around, Emmanuel demoed the Hibernate solution to DRY up your constraints.  Why maintain them separately in your DB *and* your business logic *and* your server-side UI logic *and* your client-side UI logic?  Hibernate Validator gets us closer to that single-source-of-info nirvana, and it brings with it a rather rich and flexible set of validators.  And with [JSR 303](http://jcp.org/en/jsr/detail?id=303) in progress, we should soon see a *standard* set of annotations for expressing validation rules (and I doubt it will look *much* different than the Hibernate solution we have today).

\*You can also catch Emmanuel at the [Grails eXchange](http://www.grails-exchange.com/emmanuel-bernard) in October.  

### Exploiting JRuby: Building Domain-Specific Languages for the Java Virtual Machine
Presented by [Rob Harrop](http://blog.springframework.com/rob/) (Co-author of [Pro Spring](http://www.apress.com/book/bookDisplay.html?bID=405) and VP at [Interface21](http://www.interface21.com/))

Rob Harrop started off his talk with a confession of sorts.  After explaining that the information from his talk could apply to any dynamic scripting language (e.g., [Groovy](http://groovy.codehaus.org), [Jython](http://www.jython.org/Project/index.html), etc.), he said, "I chose [JRuby](http://jruby.codehaus.org/) because Sun likes it, and that would get me here on a free ticket."  Hilarious!  Kudos to Rob Harrop for telling it like it is.  And with the JRuby guys sitting in the front row - no pressure, Rob - it was time to introduce the Java crowd to the world of [DSLs](http://en.wikipedia.org/wiki/Domain-specific_programming_language).

Rob first provided some background on DSLs in general, explaining that they aren't just about business domains (e.g., [rake](http://rake.rubyforge.org/)), they're limited in scope, and that the end goal is to provide a syntax that *clearly* expresses the solution for a highly-focused problem space.   

Because Ruby is "like putty," Rob explained, you can make it do just about anything you want.  And you have a whole host of techniques at your disposal when implementing your DSL:

*   operator overloading
*   hashes and symbols
*   [method_missing](http://ruby-doc.org/core-2.3.0/BasicObject.html#method-i-method_missing)
*   dynamic type extension (i.e., adding new methods to a class at runtime)

And rather than just talking about each technique, Rob demoed them, and showed the crowd just how simple and elegant a DSL (and its implementation) can be.  Well done, Rob.

Rob also cautioned Java developers about trying to tackle Ruby using Java patterns and idioms, encouraging them instead to try to approach Ruby from the Ruby mindset.  How, you ask?  Rob's answer: The aptly titled book by Hal Fulton, [The Ruby Way](http://www.amazon.com/Ruby-Way-Hal-Fulton/dp/0672320835).

--

And with that, we've reached the end of our week long journey.  Thanks for checking it out.  It's been a blast!
