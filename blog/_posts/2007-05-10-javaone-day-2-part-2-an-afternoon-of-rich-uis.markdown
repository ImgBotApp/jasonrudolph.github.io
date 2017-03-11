---
title: "JavaOne Day 2, Part 2: An afternoon of rich UIs"
layout: post
tags:
- grails
- java
---
For Day 2's early afternoon sessions, I had the opportunity to see two very different solutions for building rich user interfaces.

### Fast, Beautiful, Easy: Pick Three--Building Web User Interfaces in the Java Programming Language with Google Web Toolkit
Presented by Bruce Johnson and Joel Webber (Creators of GWT)

GWT was clearly one of the biggest headline grabbers coming out of JavaOne '06, and the Google guys were back and ready to convince any of the wait-and-seers that haven't yet taken it for a spin.


<!--more-->

Bruce and Joel made a good case for the many benefits of GWT and certainly got a lot of people thinking with their declaration that "GWT brings software engineering to Ajax."  While I'm definitely impressed with GWT, I'm not sure I agree with the underlying inference in that statement that other Ajax toolkits lack sound software engineering.  Granted, the *majority* of JavaScript in the wild represents a pure hack-and-slash mentality, but the [popular](http://prototypejs.org) [Ajax](http://script.aculo.us/) [toolkits](http://dojotoolkit.org/) clearly embody real software engineering and bring with them some notably elegant abstractions.

So while I'm not exactly sold on *that* particular argument for GWT, I'm certainly impressed with the toolkit itself.  The performance optimizations in particular are quite impressive, including the ability to minimize the size of the code sent to the browser, the emphasis on page-loading speeds, and the downright genius strategies for fetching/caching images.  Apparently GWT combines all of the images in your application into a single image file, gives it a unique name using a hash generated from the bytes in the file, and instructs the browser to cache it forever.  The client-side code then simply instructs the browser to render the appropriate *portion* of the image in the desired area of the page.  In doing so, GWT significantly reduces page-loading time, as the browser has far fewer requests to make to the server.  And if the application's images ever change, GWT simply generates a new consolidated image file with a new name, and all is well.

They also demonstrated a "history" feature provided by GWT.  The concept of bookmarking an Ajax app has traditionally brought with it more questions than answers.  (For example, if you never navigate to another page and the URL never changes, how do you capture the fact that you've navigated to a new tab *within* the page?)  These guys seem to have it figured out.  Very cool!

All in all, it's obvious that GWT brings some compelling (and unique) features to the RIA toolkit arena, and it definitely deserves consideration if you're in the market for an Ajax solution for your apps.

So you ask, how 'bout using GWT with [Grails](http://grails.org)?  Well, that [question](http://jira.codehaus.org/browse/GRAILS-958) is getting a fair amount of attention these days, and I suspect we'll see [something along those lines](http://www.nabble.com/How-about-grails-%2B-gwt-tf2867231.html#a8015078) in the near future.     

The Q&A session, while brief, also led to some interesting tidbits.  Most notably, when asked about support for charts and graphs in GWT, they explained that they hope to soon have client-side graphics support on par with Java 2D.  Impressive!

And speaking of Java 2D...

### Extreme GUI Makeover 2007
Presented by Romain Guy (GUI Pimp), Christopher Campbell (Java 2D Master), and Shannon Hickey (Swing Sorcerer)

After spending 8 years on the server side, it's easy to forget about Java on the desktop; so, I decided it was time to check in on that realm.  

Romain opened up the session by discussing the feedback they've gotten from previous incarnations of the Extreme GUI Makeover.  In years past, they've pimped a chat client and an e-mail client, but the attendees apparently responded that those apps aren't representative of the corporate applications that most desktop Java devs are building.  Solution?  Romain explained, "We've heard your feedback, and this year we're going to build something boring."  Ha!  

Truth be told, it was far from boring, and this 60 minutes of pure eye candy made quite a strong argument for Java on the desktop.  

–

Still more to come from Day 2.  The final installment is on its way shortly.
