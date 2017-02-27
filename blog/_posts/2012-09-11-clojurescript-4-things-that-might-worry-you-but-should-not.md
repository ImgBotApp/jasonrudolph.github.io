---
title: "ClojureScript: 4 things that might worry you, but shouldn't"
layout: post
tags:
- clojurescript
---

When I first considered taking ClojureScript for a spin, there were several things that gave me pause:
"What's the debugging experience like?"
"How often am I going to find a problem in my app, only to discover that it's actually a bug in ClojureScript?"
And so on.

I was new to ClojureScript (and fairly new to Clojure at the time as well), so I didn't take these things lightly.
Once I got started, I was pleasantly surprised with the results.
The actual experience wasn't just better than I expected; the actual experience was pretty darn good.

If you're on the fence about giving ClojureScript a shot, I hereby present: *4 things that might worry you, but shouldn't*.


## Debugging

**My worry**

ClojureScript compiles [1] to JavaScript.
Any error that occurs will be reported to me as JavaScript; probably as *horribly obfuscated JavaScript*.
How am I going to trace that error back to the root cause in my ClojureScript code?
Will I even have a fighting chance? [2]

**My experience**

Finding the *ClojureScript* code that produced a *JavaScript* error is straightforward and reasonably fast.
Despite coming to ClojureScript with little Clojure experience, it has never taken me more than 60 seconds to go from
A) seeing a JavaScript stack trace in the browser to
B) identifying the exact culprit inside my ClojureScript code.
And on average, it's much faster than that.

When an error occurs, the console shows you the error and the file where the error occurred.
When you click on the filename in the console, it takes you directly to the JavaScript line that generated the error.
(Sounds familiar, right? Browsers have worked this way for an Internet eternity or two.)

For me, the surprise came when I viewed the compiled JavaScript.
It provides all the clues you need to quickly identify the source of the problem.
For starters, the first line of the file tells you the exact ClojureScript namespace that produced the error.
Armed with that context, you're ready to look at the line of JavaScript that gave you the error.
And as it turns out, that JavaScript looks *similar enough* to your ClojureScript code that you can perform the mental mapping between the two without much effort. [3]

The following screenshots illustrate this workflow.

[![Step 1 - Observe error](http://jasonrudolph.com/resources/201209-cljs-debugging-1-thumb.png "Step 1 - Observe error")](http://jasonrudolph.com/resources/201209-cljs-debugging-1.png)
[![Step 2 - Trace it back to your ClojureScript code](http://jasonrudolph.com/resources/201209-cljs-debugging-2-thumb.png "Step 2 - Trace it back to your ClojureScript code")](http://jasonrudolph.com/resources/201209-cljs-debugging-2.png)


## API stability

**My worry**

ClojureScript is barely [a year old](https://twitter.com/jasonrudolph/status/226271633181143040). [4]
I'll bet the dev team is still rapidly evolving the API.
I don't want to have to fix my app every time I upgrade to each and every point release of ClojureScript.

**My experience**

ClojureScript benefits from the stability of *Clojure's* API.
I've upgraded the same app to new releases of ClojureScript several times.
Only once did an upgrade require changes to my application code, and even then, [those changes were minor syntax tweaks](https://github.com/jasonrudolph/one-rep-max/commit/014f8d71a99353b2b0b8490c262eea8de69a3ca3).


## Quality

**My worry**

Did I mention how young ClojureScript is?
I'm okay with "leading edge," but am I prepared for the *bleeding* that goes with "bleeding edge?"
Do I really want to be the guinea pig for some bug-ridden alpha software?

**My experience**

ClojureScript is quality software with a responsive dev team.
In eight months of working with ClojureScript, and through several ClojureScript upgrades, I've only been impacted by a single bug.
I reported that issue on the mailing list at 7:30pm on a Monday night.
Figuring that I wouldn't hear anything until the morning, I decided to go grab some dinner, and then work on something else.

Enter [David Nolen](https://twitter.com/swannodette).
Fortunately for me, David hates dinner, and he hates software bugs even more.
So for him, 7:30pm seems like a perfectly reasonable time to be churning through JIRA tickets.
Clearly my expectations were too low; David wasn't going to let me wait 16 hours for a reply.
Instead, he fixed the issue, [committed it](https://github.com/clojure/clojurescript/commit/9319579), and [replied](https://groups.google.com/d/msg/clojure-dev/I2T5Nn7gu3Q/pwpCe2IvBxEJ)—in just 42 minutes.

I've *paid* good money for support nowhere near as responsive as this!


## Performance profiling and tuning

**My worry**

What the heck am I going to do when I discover that part of my app is too slow?
I'm pretty sure there are zero ClojureScript performance profiling tools out there.

**My experience**

While you're unlikely to find a ClojureScript-specific perf tool, the [Google Chrome profiling tools](https://developers.google.com/chrome-developer-tools/docs/cpu-profiling) give you what you need. [5]

Eventually, part of my ClojureScript app became slow—unusably slow.
The Chrome profiling tools helped me track down the bottleneck. [6]
The screenshot below describes the process.

[![ClojureScript Performance Profiling](http://jasonrudolph.com/resources/201209-cljs-performance-profiling-thumb.png "ClojureScript Performance Profiling")](http://jasonrudolph.com/resources/201209-cljs-performance-profiling.png)

## Runtime tooling in general?

Debugging and performance profiling are two specific worries I had.
In each case, the existing JavaScript runtime tools were sufficient for satisfying my ClojureScript needs.
(And in both cases, I already had those tools installed—they are *built-in to the browser*!)

The landscape of JavaScript runtime tooling extends well beyond these two examples.
Is other runtime tooling similarly applicable for ClojureScript development?
Perhaps.
Where there's a runtime tool for doing *x* with JavaScript, it might just be a decent tool for doing *x* with ClojureScript as well.


## What, me worry?

I approached ClojureScript expecting each of these things to be a source of pain.
Thankfully, I was wrong.
If any of them have caused you to think twice about giving ClojureScript a try, I contend that they shouldn't.

----

## Notes

[1] "[Transpiles](http://en.wikipedia.org/wiki/Transpile)" if you're nasty.

[2] Of course, this concern is not unique to ClojureScript. It's a longstanding worry for languages that compile to JavaScript (and probably for most other compilation targets throughout the history of computing).

[3] I suspect that one day—perhaps [very soon](https://twitter.com/swannodette/status/241671008438849537)—we'll have [source maps](http://www.html5rocks.com/en/tutorials/developertools/sourcemaps/ "Introduction to JavaScript Source Maps - HTML5 Rocks") for ClojureScript.
When that day comes, we'll look back on the current workflow as "The Olden Days of ClojureScript Debugging."
You know: when we used to walk 7 miles in the snow, uphill both ways, in order to track down the source of an error.
But in all seriousness, while I look forward to having source maps for ClojureScript, the debugging experience *is* sufficient without them.

[4] Actually, my initial worry dates back to early 2012, when ClojureScript was even newer. Do I really want to dive head first into a six-month-old language?

[5] Safari, Firefox (via Firebug), and Internet Explorer offer similar functionality.

[6] It turns out that you probably don't want to construct a 30 kB string (30 kB!) for *every single event* that fires inside your app.

--

**Thanks** to [Brenton Ashworth](https://twitter.com/brentonashworth), [Stuart Sierra](https://twitter.com/stuartsierra), and [Luke VanderHart](https://twitter.com/levanderhart) for reading drafts of this post.
