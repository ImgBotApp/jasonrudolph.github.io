---
title: "JavaOne Day 3, Part 1: Mash-up your languages, mash-up your web apps"
layout: post
tags:
- agile
- java
- rails
- ruby
---
The variety of topics at this year's JavaOne has been quite impressive, and Day 3 was no exception.  Ruby, JavaScript, Groovy, Spring, and JMX all in one day?  You bet.  Here goes.  

### JRuby on Rails: Agility for the Enterprise
Presented by [Thomas Enebo](http://www.bloglines.com/blog/ThomasEEnebo) and [Charles Oliver Nutter](http://headius.blogspot.com) ([JRuby](http://jruby.codehaus.org/) Core Developers)

Charlie and Tom referred to this session as a chance to see "how the other 8% lives," and not surprisingly, this talk saw a fair amount of traffic.  When they polled the audience though, it was quite interesting to see that more folks had heard of Rails than had heard of Ruby.  (I imagine the Ruby veterans find that bit of trivia to be a bit annoying.)


<!--more-->

The demoes were well done, and it was certainly cool to see a Rails app running on GlassFish.  Once you use [GoldSpike](http://www.headius.com/jrubywiki/index.php/Rails_Integration) to produce a WAR from your Rails app, well, at that point, it's just another WAR.  Pretty cool stuff.

Since one of the big motivations for JRuby is the ability to call into the multitude of available Java libraries, I've been curious to see what the resulting code would look like in JRuby.  Good Ruby code tends to look downright elegant, so I couldn't imagine any Ruby dev would want to see Java idioms creeping into their otherwise beautiful Ruby code.  And from the looks of it, JRuby does a pretty good job of keeping the Ruby idioms intact.  A Ruby developer needn't bother uglying up their code with something foreign like `compareToIgnoreCase()`; they can simply write the more conventional `compare_to_ignore_case` and JRuby handles the translation.  Good stuff.

If you can draw any one conclusion from this renewed interest in dynamic languages, I'd have to say it's that the ability of these languages to vanquish so many of the pain points of Java development is resonating quite loudly with the Java crowd (myself included).  The promise of a more pleasant and - dare I say it? - fun development experience sure has the aura of a shining city on a hill.  But it took us actually *seeing* these other languages to finally challenge the status quo.  That's just one more argument for the timeless advice from [The Pragmatic Programmer](http://www.pragmaticprogrammer.com/loty/):  "Learn at least one new language every year."  So, which one will you choose for 2007?

### Blueprints for Mash-ups: Practical Strategies, Tips, and Code for Designing and Building
Presented by [Sean Brydon](http://weblogs.java.net/blog/sean_brydon/) (Technical Lead for the [Java BluePrints Program](http://java.sun.com/blueprints) at Sun Microsystems), [Gregory Murray](http://weblogs.java.net/blog/gmurray71/) (Ajax Architect at Sun Microsystems and Creator of Project [jMaki](https://ajax.dev.java.net/)), and [Mark Basler](http://blogs.sun.com/basler/) (Senior Software Engineer at Sun Microsystems and Member of the [Java BluePrints Program](http://java.sun.com/blueprints))

For anyone wanting a good run-down on the various technologies fueling mash-ups - at least from the perspective of a Java developer - and the design considerations when selecting between those technologies, this was the talk to see.  Should I use REST or SOAP?  XML or JSON?  What about JSONP?  Do I want to do the [monster mash](http://en.wikipedia.org/wiki/Monster_Mash) on the server side or the client side?  

Curious what the speakers recommend? If so, be sure to check out the [slides](http://developers.sun.com/learning/javaoneonline/j1sessn.jsp?sessn=TS-6676&yr=2007&track=8)*, as they do a good job of capturing the highlights.  

*Sun says, "For non-attendees, the downloads will be made available at [JavaOne Online](http://developers.sun.com/learning/javaoneonline/) approximately two weeks after the conference."

--

And with that, the Day 3's AM sessions are a wrap.  Still more to come from the PM talks.
