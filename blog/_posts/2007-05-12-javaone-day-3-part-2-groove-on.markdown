---
title: "JavaOne Day 3, Part 2: Groove on!"
layout: post
tags:
- grails
- groovy
- java
---
Groovy's getting a whole lotta love at the JavaOne bookstore this week, and as of this moment, [Groovy in Action](http://www.manning.com/koenig/) is #5 on the JavaOne [best seller list](http://java.sun.com/javaone/sf/2007/articles/bookstorebestsellers.jsp).  Groovy's been at least *mentioned* in almost every session I've seen, and as you can tell from the titles of the talks below, these particular sessions gave it much more than just a passing comment.

### Advanced Groovy
Presented by [Rod Cope](http://www.openlogic.com/blogs/author/rod/) (CTO and Founder of [OpenLogic](http://www.openlogic.com/))

Two-time JavaOne rockstar Rod Cope pulled out all the stops in this talk, and given the wow-factor of this session, I'll be quite surprised if he doesn't three-peat his rockstar status.


<!--more-->

Considering that most folks are still impressed with the basics of [Groovy](http://groovy.codehaus.org/) (and rightfully so), I was eager to see how advanced this presentation would be and how that advanced nature would be received.  For sure, the talk lived up to its title.  The concepts of [currying](http://groovy.codehaus.org/Blocks,+Closures,+and+Functions#Blocks%2CClosures%2CandFunctions-ParameterDefaulting%2CCurrying%2CandNumberVarying) and aliasing, for example, are certainly foreign to most Java developers, but Rod somehow found a way to demystify and demonstrate these features in clean and simple fashion.  After explaining these and other concepts via slides, it was time to show off the power of Groovy with the most gutsy demo I saw all week.  

The Groovy shell ([groovysh](http://groovy.codehaus.org/Installing+Groovy)) is a great tool for small experiments, but for anything more than a few lines, I personally feel much more comfortable in the Groovy console or just running a script in [TextMate](http://docs.codehaus.org/display/GROOVY/TextMate).  With the Groovy shell, if you notice that you made a typo three lines ago, there's no easy way to go back and fix it;  you're basically back at square one. So doing a live and complex demo with the Groovy shell is pretty much the programmer's equivalent of walking a tightrope without a net.  Rod must have felt especially well-balanced, because he nailed it!  He demoed how you can create an XML RPC server and client from scratch and have them communicate with one another in just seven lines of Groovy code.  Awesome!  And as if that wasn't cool enough, he then showed off how you can add a new method to the *running* server (without restarting it) and instantly start calling that method from the client....and the crowd goes wild!  

But Rod's obviously not the type that's satisfied with just one cool demo.  No.  He wanted more.  From there it was time to show off [COM scripting](http://groovy.codehaus.org/COM+Scripting) with Groovy, and in about thirty lines of code, Rod demoed the ability to open Excel, add a new workbook, populate cells, change fonts, create a chart, add a tile and legend, and even export the chart to a Swing app.  Well done, Rod!  Rock on!

If you didn't get a chance to see this session, you're not out of luck; you'll have another opportunity to catch Rod in action at the [Grails eXchange](http://www.grails-exchange.com/rod-cope) later this year.  So reserve your spot now, and I'll see you there!  

### Creating Manageable Systems with JMX, Spring AOP, and Groovy
Presented by [Vladimir Vivien](http://www.nofluffjuststuff.com/speaker_view.jsp?speakerId=2061) (Senior Software Engineer at [Simplius LLC](http://simpli.us/))

Application manageability is one of those things that almost never makes it into the system requirements, yet almost every non-trivial application needs a management component of one form or another. Vladimir's argument for taking the time to build in manageability was well put:  "By the time you see something in a log file, it's already too late."  And after his demonstration of how little effort is needed to introduce management into a Java application, I suspect many of us in the audience will be giving it more consideration going forward.

The demo started off with a plain Java + [JMX](http://java.sun.com/javase/technologies/core/mntr-mgmt/javamanagement/) example that was pleasantly straightforward and likely enough to serve many application administration needs.  After adding [Spring](http://springframework.org/) to the mix, it got even easier.  But Vladimir still had one more way to simplify the process; it was time to bring in Groovy.  By using Spring to wire a Groovy class into the application, he no longer had to implement the MBean in Java; instead, he was able to use Groovy.  Now that's just plain cool!  

After the session, I had a chance to talk to [Guillaume](http://glaforge.free.fr/weblog/) about this use of Groovy, and he pointed me towards an easter egg of sorts buried in the Groovy code base.  What's this [GroovyMBean](http://groovy.codehaus.org/xref/groovy/util/GroovyMBean.html ) class all about?  I'll have to check that out soon.  

--

And with that, another solid day at GeekU has come to a close.  The fourth and final day awaits...
