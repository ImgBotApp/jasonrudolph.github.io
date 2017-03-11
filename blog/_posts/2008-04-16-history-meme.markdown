---
title: history meme
layout: post
tags:
- capistrano
- command line
- git
- rails
- ruby
- textmate
---
[Rob dared me](http://robsanheim.com/2008/04/16/history-meme-onwards/ "Panasonic Youth - history meme onwards") to fire up my favorite shell and jump into [the game](http://www.google.com/search?q=history+meme "history meme - Google Search").  Imagine my disappointment when I was greeted with this bummer of an error message.

![20080416 History Meme Commodore 64](/resources/20080416-history-meme-commodore-64.png)

Hmm.  No dice.  OK, on to my second choice.

<pre lang="text">
jason@jmac:~> history | awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' | sort -rn | head
48 cd
30 exit
29 m
20 ls
18 git
13 mman
12 **
10 cap1
9 ssh
9 rake
</pre>          

The result?  A few well-known friends and some that likely deserve a bit of elaboration.  

* <code>m</code> is an alias for the [mate shell command](http://macromates.com/textmate/manual/using_textmate_from_terminal#shell_terminal "Calling TextMate from Other Applications — TextMate Manual") for TextMate
* <code>mman</code> is that [handy TextMate man page viewer we talked about recently](http://jasonrudolph.com/blog/2008/03/14/manning-up-textmate-meets-man-pages/ "jasonrudolph.com - Manning up: TextMate Meets Man Pages")
* The one that's bleeped out (i.e., `**`) is an alias that takes me straight to the source dir for my current client project
* <code>cap1</code> is, um, a reminder that [deprec2 is gonna be a nice upgrade](http://www.deprec.org/#Quickstart "deprec - Trac")
