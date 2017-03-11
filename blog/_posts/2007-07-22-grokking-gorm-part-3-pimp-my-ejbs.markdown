---
title: "Grokking GORM - Part 3: Pimp my EJBs"
layout: post
tags:
- grails
- groovy
- java
---
Having tackled the [conventional approach to Grails domain models](http://jasonrudolph.com/blog/2007/07/20/groking-gorm-part-1-conventional-thinking/ "Grokking GORM - Part 1: Conventional Thinking") as well as [an XML-based solution for hooking Grails up to a non-conforming schema](http://jasonrudolph.com/blog/2007/07/21/groking-gorm-part-2-no-schema-left-behind/ "Grokking GORM - Part 2: No Schema Left Behind"), it's time to consider another option.  

Whether you're disheartened by writing too much XML (and prefer annotations instead), or you're looking for a domain model solution you can use both with Grails and without Grails, EJB3 entity beans will get your where you want to be.  In [“Advanced Domain Models in Grails”](http://www.nofluffjuststuff.com/speaker_topic_view.jsp?topicId=609), we’ll see the exact steps needed to take your plain ol' statically-typed EJBs, and equip them with the dynamic superpowers of Grails domain classes (all without adding a single line of code to those poor POJOs).  Feel free to download the [sample app](http://jasonrudolph.com/downloads/presentations/Advanced_Domain_Models_in_Grails-Example_Code.zip) and take it for a spin.  (Be sure to have a look at the included README files for all the details.)

Don't have any EJB3 entity beans to use with Grails yet?  No problem.  The Ant script included in the download (and first discussed in [yesterday's post](http://jasonrudolph.com/blog/2007/07/21/groking-gorm-part-2-no-schema-left-behind/ "Grokking GORM - Part 2: No Schema Left Behind")) not only includes the ability to reverse engineer Hibernate mapping files from a database schema, but also to produce EJB3 entity beans based on the schema.  Once again, you'll likely want to tweak the output somewhat to get your classes looking just the way you want them, but compared to *manually* performing the DB-to-POJO mapping, this tool is incredibly handy.  (Thanks again to Raffaele Castagno for providing this script.)

Knowing that Grails embraces convention over configuration, is there any room left for a *fourth* part to this series?  (Hint:  "Convention *over* configuration" != "Convention *instead of* configuration.")
