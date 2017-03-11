---
title: "JavaOne Day 4, Part 1: Where do standards come from?"
layout: post
tags:
- grails
- java
- rails
---
The fourth and final day of JavaOne: it was a big one.  Here we go...

### Comparing the Developer Experience of Java EE 5.0, Ruby on Rails, and Grails: Lessons Learned from Developing One Application
Presented by [Tom Daly](http://blogs.sun.com/tomdaly/) (Senior Performance Engineer at Sun Microsystems) and [Damien Cooke](http://blogs.sun.com/damien/category/Java) (ISV Engineering at Sun Microsystems)

Having spent many years now developing applications in the JEE space, and having had a good look at [Rails](http://www.rubyonrails.org/) before spending the past year working with [Grails](http://grails.org/), I was eager to see whether others have drawn the same conclusions as I have.  It's a time-tested technique to loosen up the crowd with a joke, and when I heard Tom's opening line - "I don't know much about Ruby and I don't know much about Groovy" - I was a bit concerned.  It wasn't meant to be a joke.  Yet somehow, in just 60 minutes, they actually managed to pull off a pretty darn fair comparison of the three frameworks.


<!--more-->

Tom started out with a quick run-down of each of the three frameworks.  (Well, he didn't bother with JEE, but given the audience, that seemed like an appropriate omission.)  There were a few glitches with the slides that discussed Groovy, but I heard more than one presenter this week comment that the slides on their screen weren't *exactly* the slides they provided to Sun before the presentation.  So, it's possible that their original slides had it right.  Either way, here's a quick look at the "errata" and some (hopefully) helpful clarifications.

* *"Groovy is a JavaScript programming language."*  Tom looked a bit surprised when he first saw this slide appear on the screen.  I'm sure they meant to say that Groovy is a dynamic language for the Java platform, sometimes referred to as a scripting language.
* *The coding samples on the slides showed semicolons terminating every line.*  It's downright awesome just how forgiving Groovy is.  You want to use semicolons?  No problem.  You don't want to use semicolons?  No problem.  Of course, Groovy is all about making our lives easier, so idiomatic Groovy omits anything that's unnecessary (including semicolons as line terminators).
* *The slides listed the file name as `Subscriber.groovey`.*  Surely that was just a typo, and actually, Groovy wouldn't reject such a file.  But for anyone new to Groovy, file names tend to end in `.groovy`.

After discussing the high-level concepts of the three technologies under review, it was time to demonstrate the effort required to build a quick CRUD app with each one.  The Rails and Grails demoes were straightforward (of course), and even the process for the JEE application wasn't as laborious as I'd expected it to be, though I cringed at the *hundreds* of lines of code and configuration the NetBeans generator spewed out.  *DRY* it was certainly not.

While they commented a bit on the developer experience, Tom explained that their real incentive for this exercise was to understand how each of these frameworks performs.  They showed some initial benchmarks illustrating exactly what you'd expect:  as a general rule, JEE tends to outperform Grails which tends to outperform Rails.  (For a more detailed benchmarking of Grails and Rails performance, check out the [results](http://grails.org/Grails+vs+Rails+Benchmark) from some tests performed just a few weeks back.  Be sure check out Graeme's comments in the summary as well, specifically the note that "Grails hasn't undergone much optimisation at all yet and there are certainly areas we can improve on.")  

They expressed concerns about how Rails and Grails apps would scale compared to a typical JEE application, and they questioned the risk of adopting a framework that's not based on a universally-accepted standard.  They didn't have any findings to report yet on the scalability, so hopefully we'll see that information soon.  And with regards to standards, if EJBs taught us anything, it's that the best standards come from solutions that have been proven in the wild (*before* they were ever a standard).  Innovation *leads* to viable solutions which lead to standards (de facto or formalized), but we simply cannot expect to start with a standard.

On a few occasions Tom raised questions about how to make a Rails or Grails CRUD application work after you've made changes to the model.  The *real* power of Rails and Grails isn't their support for CRUD (even though it makes for easy demoes), but nevertheless, this question comes up from time to time.  Thankfully, there's a simple solution for both Rails and Grails:  If you want your views to continue to automatically stay in sync with your database/domain model changes, use [dynamic (i.e., declarative) scaffolding](http://grails.org/Scaffolding#Scaffolding-DynamicScaffolding), not the [static (i.e., generated) scaffolding](http://grails.org/Scaffolding#Scaffolding-GeneratingControllers%26Views) that these demoes employed.  Once you generate the views, you've essentially "hard-coded" the specific fields into your views.  If you change your database/domain model, you need to update your views accordingly.  This process isn't unique to Rails or Grails; you'll do that same work in JEE, PHP, etc.  Also, if you haven't *customized* the static scaffolding, you can always just regenerate the static scaffolding, and the new views will then reflect the changes in your database/domain model.  

If you really want to use the scaffolding, I prefer to start with the dynamic scaffolding, and get your domain model as far along as possible before switching over to static scaffolding.  Get all your fields just as you want them, define the relationships, specify your constraints, and *then* generate the controllers and views.  For an example of this approach in action, check out Chapter 3 of [Getting Started with Grails](http://www.infoq.com/minibooks/grails).  (You can download the PDF for free, so have at it!)

Their biggest concern about Groovy and Grails seemed to involve a lack of tool support.  While most [IDEs](http://groovy.codehaus.org/IDE+Support) (and many text editors) provide at least some level of support today, they'll be happy to know that big things are on the way from each of the [major](http://jasonrudolph.com/blog/2007/04/30/groovy-11-beta-1-released-takes-java-integration-to-the-next-level/) [3](http://blogs.sun.com/geertjan/entry/javaone_day_three) [IDEs](http://jasonrudolph.com/blog/2007/05/09/javaone-day-1-javautilrandom-observations/) very soon.  

Overall, I give kudos to Tom and Damien for delivering a remarkably fair and unbiased report.  Despite their few concerns about Grails, they spoke highly of the code samples provided on [grails.org](http://grails.org/Quick+Start) and even mentioned a [certain article on integrating your EJB3 entity beans with Grails](http://www.infoq.com/articles/grails-ejb-tutorial).  Cool!  

### Taking Java Technology to New Frontiers: Enterprise Batch Processing with Spring Batch
Presented by [Rod Johnson](http://blog.interface21.com/main/author/rodj/) (Creator of the [Spring Framework](http://www.springframework.org/) and CEO of [Interface21](http://interface21.com/)), Wayne Lund (Accenture), and Scott Wintermute (Accenture)

In his opening for this talk, Rod Johnson described Java batch technology as "a missing enterprise capability in the market" and observed that the lack of a commonly-accepted architecture has led to a proliferation of expensive one-off, in-house custom solutions.  I couldn't agree more.  

Enter [Spring Batch](http://www.springframework.org/spring-batch).  We should see the first release of this new component in the next few weeks, and in classic Interface21 style, it sounds like we'll soon have a solid and feature-rich solution for this long-ignored domain.  What does it have to offer?  Quite a bit, it seems.  

*   Elegant recovery strategies (including automatic retry after failure)
*   Flexible support for a variety of message formats (e.g., fixed length, delimited, XML)
*   A "job control language" for starting, stopping, suspending, and canceling jobs.  (JCL.  Funny.  Mainframe folks should get a kick out of that.)
*   Using JMX to tweak job settings at runtime (e.g., adjusting commit intervals)
*   A DSL for batch processing, making first-class citizens out of terms like "job," "step," "module," etc.

Having lived through more than a few home-grown implementations of batch processing, I'm looking forward to checking out the new kid on the block.  

As a side note, when discussing XML processing, it was pretty darn cool to hear one of the Accenture guys give a shout out to the Groovy [XMLSlurper](http://groovy.codehaus.org/Reading+XML+using+Groovy%27s+XmlSlurper).  If you have a need to process XML in Java, you owe it to yourself to take the Groovy [XMLSlurper](http://groovy.codehaus.org/api/index.html) for a spin.   

--

One more entry still to come.  Stay tuned for the final installment.
