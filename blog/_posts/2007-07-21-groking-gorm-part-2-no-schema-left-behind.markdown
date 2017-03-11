---
title: "Grokking GORM - Part 2: No schema left behind"
layout: post
tags:
- grails
- groovy
- java
---
We began [Part 1 of this adventure](http://jasonrudolph.com/blog/2007/07/20/groking-gorm-part-1-conventional-thinking/ "Groking GORM - Part 1: Conventional Thinking") with a greenfield application that chose to kindly comply with all the standard Grails conventions.  Now it's time to venture into the land of non-conformity.  

We first looked at [hooking Grails up to a non-standard schema](http://jasonrudolph.com/blog/2006/06/20/hoisting-grails-to-your-legacy-db/ "Hoisting Grails to Your Legacy DB") over a year ago now, way back in the days of Grails 0.1.  This clearly remains a topic of much interest, as that tutorial has held its ground week in and week out for 13 straight months as the most highly-trafficked post on this site.  Grails has seen significant progress since then, so an updated example is certainly in order.

In [“Advanced Domain Models in Grails”](http://www.nofluffjuststuff.com/speaker_topic_view.jsp?topicId=609), I’ll demo the exact steps needed to gain all the dynamic persistence goodness that GORM has to offer, regardless of whether your schema plays nicely with the Grails conventions.  With just a sprinkling of configuration - 5 minutes of effort or less - we'll be up and running.  In fact, you can download and try out the app [now](http://jasonrudolph.com/downloads/presentations/Advanced_Domain_Models_in_Grails-Example_Code.zip). (Be sure to have a look at the included README files for all the details.)

To make this process even easier, the download includes an Ant script developed by Raffaele Castagno for reverse engineering the schema to produce the initial Hibernate mapping files for you.  The resulting HBM files will need a bit of tweaking (as you would expect, since the whole point of this exercise is that your schema doesn't map cleanly to your domain classes), but compared to coding up the HBM files from scratch, this tool is *incredibly* handy.

Keep an eye out for Part 3, where we invite EJB3 entity beans to the party.  Stay tuned.
