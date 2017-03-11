---
title: "Manning up: TextMate meets man pages"
layout: post
tags:
- command line
- textmate
---
Navigating through [man pages](http://en.wikipedia.org/wiki/Manpage "Manual page (Unix) - Wikipedia") in a terminal window doesn't exactly rank as a highlight of this developer's day.  The experience feels like [1971](http://en.wikipedia.org/wiki/Manpage#History "History of Man Pages - Wikipedia") for a reason, and that means of interaction just leaves something to be desired.  Perhaps you could make the argument that A) people that read man pages don't rank humane interfaces as a top priority, or that B) I could spend more time mastering the ways to navigate via [less](http://en.wikipedia.org/wiki/Less_%28Unix%29 "less (Unix) - Wikipedia") (the default man page browser in OS X).  But, believe it or not, apparently I'm not alone in my crazy desire to [consult man pages outside of the terminal](http://www.tuaw.com/2008/03/07/here-comes-your-man-viewer/ "Here comes your man (viewer) - The Unofficial Apple Weblog (TUAW)").  So with [web-based solutions](http://www.hmug.org/man/ "HMUG: man Pages"), [PDF generators](http://www.daniele.ch/man2PDF.zip "man2PDF -	"Create beautiful PDF files from the man pages""), and [full](http://www.kendallp.net/at_PAK/ManViewer/ "Man Viewer")-[blown](http://geeksuit.com/software/77_0_1_0_M/ "Man Handler") [apps](http://www.clindberg.org/projects/ManOpen.html "ManOpen") dedicated solely to "manning up," where should we turn?  Queue [The Pragmatic Programmer](http://pragmaticprogrammer.com/the-pragmatic-programmer/extracts/tips "Pragmatic Software Development Tips from the "Pragmatic Programmer"") for some welcome words of wisdom:

> **Use a Single Editor Well**
>
> The editor should be an extension of your hand; make sure your editor is configurable, extensible, and programmable.

For me, that editor is undoubtedly [TextMate](http://macromates.com/ "TextMate — The Missing Editor for Mac OS X").  I already spend most of my day in TextMate, be it for [coding](http://thinkrelevance.com/ "Relevance, Inc."), [blogging](http://blog.macromates.com/2006/blogging-from-textmate/ "TextMate Blog - Blogging From TextMate"), editing wiki pages (and other [Safari-based content](http://macromates.com/textmate/manual/using_textmate_from_terminal#cocoa_text_fields "Calling TextMate from Other Applications — TextMate Manual - Cocoa Text Fields")), or sometimes even [writing e-mail](http://www.hawkwings.net/2006/04/26/using-textmate-as-editor-in-mailapp/ "Hawk Wings - Using TextMate to edit emails in Mail.app").  So, if I can use TextMate to find my way around a man page, that's an all-around win.  

## Goal

While working in the terminal, be able to quickly open a man page in TextMate.

## Making it happen

First, [install the mate shell command](http://macromates.com/textmate/manual/using_textmate_from_terminal#shell_terminal "Calling TextMate from Other Applications — TextMate Manual").  (Even if you have no interest in viewing man pages in TextMate, this command is simply indispensable for anyone that even occasionally ventures into the land of the terminal.)

Now that we have access to TextMate from the command line, we can assemble a quick script to get us the rest of the way toward achieving our goal.  I keep all of my custom scripts in a <code>.scripts</code> directory that I include in my path, so I'll define this handy scriptbaby in a file named <code>mman</code> (for "mate man") in that directory.

<pre lang="text">
$ ls -l /Users/jason/.scripts/mman
-rwxr-xr-x@ 1 jason  jason  43 Mar 14 15:52 /Users/jason/.scripts/mman
</pre>

And once we drop a bit of Unix-fu into that file, we'll be good to go.

<pre lang="text">
#!/usr/bin/env bash

man $1 | col -b | mate
</pre>

To see it in action, just use <code>mman</code> anywhere you would have previously used the vanilla <code>man</code> command.

[![Running mman in Terminal to open man page in TextMate](/resources/20080314-mman-textmate-thumb.png)](/resources/20080314-mman-textmate.png)

## Kicking it up a notch?

That approach has served me well for several months now, but in the course of writing this post, I came across an associated TextMate bundle that some folks may find helpful as well.  The TextMate [Man Pages bundle](http://fisheye2.cenqua.com/changelog/textmate-bundles/trunk/Bundles/Man%20Pages.tmbundle) offers some (minor) syntax highlighting, the ability to open a man page from *within* TextMate, and the ability to use Command + Shift + T (i.e., ["Go To Symbol"](http://macromates.com/textmate/manual/navigation_overview.html#function_pop-up)) to quickly find and access key sections of the man page by name.

[![Showing off the TextMate man page bundle](/resources/20080314-mman-with-textmate-bundle-thumb.png)](/resources/20080314-mman-with-textmate-bundle.png)      

Now go forth and devour some man pages already.
