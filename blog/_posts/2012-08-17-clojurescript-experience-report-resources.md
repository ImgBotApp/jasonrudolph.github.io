---
title: "ClojureScript experience report: Resources"
layout: post
tags:
- clojurescript
- speaking
---

Thanks to everyone who came out to the [Triangle Clojure Users Group](http://www.meetup.com/TriClojure/events/71707312/ "A ClojureScript Experience Report -  The Triangle Clojure Users Group (Durham, NC) - Meetup") for my talk last night.
It was great to see all the [enthusiasm for ClojureScript](https://twitter.com/rippinrobr/statuses/236276363064127490).

For those that want to dig in further, here are the resources I mentioned:

- [One Rep Max](https://github.com/jasonrudolph/one-rep-max) — an open source ClojureScript app; the source of the experience behind this "experience report"
    - [Network architecture](https://github.com/jasonrudolph/one-rep-max/blob/ca4d600/doc/network-architecture.png)
    - [A sample event flow](https://raw.github.com/jasonrudolph/one-rep-max/b16c82e/doc/create-set-event-flow.png)
- [ClojureScript One](http://clojurescriptone.com/ "ClojureScript One Guide")
    - [one.dispatch](http://clojurescriptone.com/documentation.html#one.dispatch "ClojureScript One Documentation - one.dispatch") — event dispatching library
    - [Design mode](https://github.com/brentonashworth/one/wiki/Design-and-templating)
- [Domina](https://github.com/levand/domina) — DOM manipulation library
- Converting from JSON to Clojure data and vice versa
  - [`js->clj`](https://github.com/clojure/clojurescript/blob/r1450/src/cljs/cljs/core.cljs#L6587) (from cljs.core)
  - [`clj->js`](https://github.com/jasonrudolph/one-rep-max/blob/5090de2/src/app/cljs/one/repmax/util.cljs#L5) (from [Chris Granger](https://twitter.com/ibdknox)'s [fetch](https://github.com/ibdknox/fetch) library)
- [Shoreleave](https://github.com/ohpauleez/shoreleave) — up-and-coming collection of ClojureScript libraries
- [ClojureScript: Up and Running](http://shop.oreilly.com/product/0636920025139.do "ClojureScript: Up and Running — By Stuart Sierra and Luke VanderHart") — soon-to-be-beta book from [Stuart Sierra](https://twitter.com/stuartsierra) and [Luke VanderHart](https://twitter.com/levanderhart)

Enjoy!
