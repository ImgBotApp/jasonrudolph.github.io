---
title: "JavaOne Day 1: java.util.Random observations"
layout: post
tags:
- grails
- groovy
- java
- ruby
---
A very full first day is in the books. Here we go...

### Sun keynote
The conference officially kicked off with the 2-hour "Sun General Session."  

* F3 gets rebranded as JavaFX, but will people in the Silverlight and Flex camps even give it a thought?
* JRuby's getting a whole lotta love from Sun.  They specifically called out JRuby in at least two instances (including official support for it in Glassfish V2).  

On to the tech sessions...

### Cool Things You Can Do With the Groovy Dynamic Language
Presented by Guillaume Laforge ([Groovy](http://groovy.codehaus.org) Project Lead) and Dierk Koenig (Lead Author of [Groovy in Action](http://www.manning.com/koenig/))

* 600 people + a waiting list
* Called in "air traffic controllers" to guide people into the room
* Dierk: "Kind of like saying, 'Please tell me everything you can do with Java.  You have 60 minutes."
* Good demoes on how Groovy eases many of the pain points and eliminates much of the noise in day-to-day Java development

I also had the privilege of sitting next to Alex Tkachman (from JetBrains) during the talk, and I got to see a quick demo of the up-and-coming Grails plug-in for IntelliJ IDEA v7.  To those of you calling for better tool support for Groovy and Grails, suffice it to say that your voice has *clearly* been heard.  

### *Java Puzzlers*, Episode VI: The Phantom-Reference Menace/Attack of the Clone/Revenge of the Shift
Presented by Josh Bloch (Chief Java Architect at Google and Author of [Effective Java](http://java.sun.com/docs/books/effective/)) and Bill Pugh (Professor of Computer Science at the University of Maryland and founder of [FindBugs](http://findbugs.sourceforge.net/))

* Huge room.  Slam-packed.  1000 attendees?  1200?  Huge.
* We should all study the presentation skills demonstrated by Josh Bloch and Bill Pugh.  These guys are true rockstars.  
    * Solid, polished speakers
    * Somehow able to explain tedious features of Java, and do so in a way that's fun and, at times, downright hilarious
* Presented the "moral" of each puzzle
* FindBugs already identifies each and every one of these evasive corner cases of the Java language:
    * "The Joy of Sets"     
        * Sets + generics + some hidden gotchas
        * Moral - Avoid `short` types.  (Primitive types that is, not midgets.)
    * Goodbye, URL
        * In java.net.URL, [`hashCode`](http://java.sun.com/j2se/1.5.0/docs/api/java/net/URL.html#hashCode() and [`equals`](http://java.sun.com/j2se/1.5.0/docs/api/java/net/URL.html#equals(java.lang.Object) are over-engineered and, as a consequence, they happen to be broken.
        * Moral - Use URI. (Avoid URL and over-engineers.)
    * JUnit vs. Threads    
        * JUnit doesn't support testing concurrency.
        * Moral - Working software leads to [currency](http://en.wikipedia.org/wiki/Currency).  ;-)
    * Recursive Initialization vs. Auto-unboxing  
        * Yes.  We're deep in Geektown now.  Good stuff.
        * Moral - Create the Singleton instance *after* all static field initialization statements.
    * Low-level Bit-twiddling with java.io
        * [java.io.InputStream#skip](http://java.sun.com/j2se/*5.0/docs/api/java/io/InputStream.html#skip(long) is darn close to evil
        * Morals
            * Ignore return values at your own risk and peril.
            * For API designers:
                * Don't violate the principle of least astonishment.
                * Make it easy to do simple things.  (If only there were a language that followed this mantra [out-of-the-box](http://groovy.codehaus.org).)
    * Fun with `Math.abs`
        * `Integer.MIN_VALUE == -Integer.MIN_VALUE`     
        * Moral - [java.lang.Math#abs](http://java.sun.com/j2se/*5.0/docs/api/java/lang/Math.html#abs(int) doesn't guarantee a non-negative result.
    * Ternary Operator vs. Numeric Values
        * Using mixed numeric types with the ternary operator can be a recipe for trouble
        * Moral - `: ?` is not always equivalent to `if/else`

### Open-Source Licensing Emergency Room Panel
Presented by Simon Phipps, Cliff Schmidt, and Eben Moglen

* Interesting state-of-the-union on the various open source licensing philosophies and plans for avoiding an influx of new license models (presumably all offering slight variations on existing licenses)

### Integration Gets All Mashed Up: Bridging Web 1.0 and Web 2.0
Presented by Andreas Krohn

* Defined a mash-up as the "the ad-hoc assembly of situational apps"
* Made the case for mash-ups as an enterprise solution (to provide access to disparate systems with conflicting or non-existent APIs)
* Discussed the enabling technologies behind the mash-up phenomenon (and some standards that may come into play in the future)
    * Atom vs RSS
        * No compelling reason to continue supporting RSS
        * Atom is a true standard (as opposed to the 13-ish flavors of RSS)
        * Atom can carry payloads other than plain text (e.g., binaries)
    * Atom Publishing Protocol (APP)
        * Supports REST, user authentication, etc.
        * Example: Google Data API
    * JSR 311 - Java API for RESTful Web Services
    * Tools to check out
        * [Feed43](http://feed43.com/) - Produces RSS feed from any web page
        * [openkapow](http://openkapow.com) - Kinda like OS X Automator for slicing and dicing websites to produce web services from them
* Makes for cool demoes and certainly has several practical uses, but the model just seems too fragile for *corporate* use.  Would you honestly want to support an app that fetches its data via the web equivalent of screen scraping and *assumes* that the underlying web page (whose author you've never spoken to) won't change its structure?  

### JetBrains "BoF"
You won't find this one on the session schedule, but it was by far the highlight of the day.  This "mash-up" of the Groovy & Grails guys, NFJS guys, and JetBrains guys was the sort of ego-free exchange of ideas that progresses our industry.  Many thanks to the kind folks at JetBrains for putting together this event.  Well done!

--

Day 2 starts in 2 hours.  Stay tuned.
