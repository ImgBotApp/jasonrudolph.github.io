---
title: "Testing anti-patterns: Underspecification"
layout: post
tags:
- code coverage
- testing
- testing anti-patterns
---
Last week we discussed the perils of [overspecification](http://jasonrudolph.com/blog/2008/07/01/testing-anti-patterns-overspecification/ "jasonrudolph.com/blog -- Testing Anti-patterns: Overspecification"), and while we saw that it's clearly possible for a test suite to do too much, it's far more common for it to do too little.

## [Green](http://dictionary.cambridge.org/define.asp?key=34369&amp;dict=CALD "green (adjective): novice, inexperienced, perhaps even naive") architecture

Suppose we're building an application for an online retailer, and they decide that they want to provide free shipping on all orders with a minimum price of $25.00.  (Where do they come up with this stuff?!)  Armed with these requirements, we set off to develop the logic to determine whether a given order qualifies for this new offer.  (We'll pick on some half-baked Ruby code for this example, but we could certainly extrapolate the same ideas to any language we might choose.)

It's a straightforward request, so we'll crank out a quick method to encapsulate the logic ...

```ruby
MIN_FREE_SHIPPING_PRICE = 25.0   

def free_shipping?(total_order_price)
  total_order_price > MIN_FREE_SHIPPING_PRICE
end
```

... and add a few simple tests to make sure we're getting the desired results (all the while being careful to avoid any *over*specification, of course).

```ruby
def test_free_shipping_returns_true_for_order_above_min_price
  assert free_shipping?(MIN_FREE_SHIPPING_PRICE + 1)
end

def test_free_shipping_returns_false_for_order_below_min_price
  assert !free_shipping?(MIN_FREE_SHIPPING_PRICE - 1)
end
```

And just like that, we have a passing test suite ...

```
$ ruby underspecification_test.rb
Loaded suite underspecification_test
Started
..
Finished in 0.00029 seconds.

2 tests, 2 assertions, 0 failures, 0 errors
```

... and 100% code coverage ...

![100% Test Coverage](/resources/20080708_underspecification_coverage_report.png "100% Line Coverage, 100% Branch Coverage, and 100% Path Coverage")

... so there's certainly the temptation to declare victory.

![Mission (Not Exactly) Accomplished](/resources/20080708_underspecification_mission_accomplished.png "Mission (Not Exactly) Accomplished")

But what about the customer that just spent the last 20 minutes concocting the perfect order?  You know, the one that's exactly $25.00 and not a penny more.  (Sure, he needs professional help, but do you really want to get on the wrong side of someone with that kind of determination and time on their hands?)  If we're looking for our test suite to tell us how the application should respond to a $25.00 order, we're out of luck.  This **underspecification** means that our test suite not only *fails to communicate* how the application should behave in this scenario, our test suite also *fails to give us any confidence* that the application will do the right thing (whatever that may be).

## Edge cases matter

Since we're calling it a "minimum" price, it sure sounds like a $25.00 order *should* qualify for free shipping, so we *should* add a test to specify that behavior.

```ruby
def test_free_shipping_returns_true_for_order_equal_to_min_price
  assert free_shipping?(MIN_FREE_SHIPPING_PRICE)
end
```

And when we run this test, we should get some good insight into whether we're likely to have that rather obsessive customer hunting us down in his copious free time.

```
$ ruby underspecification_test.rb
Loaded suite underspecification_test
Started
..F
Finished in 0.007163 seconds.

  1) Failure:
test_free_shipping_returns_true_for_order_equal_to_min_price(UnderspecificationTest) [underspecification_test.rb:16]:
<false> is not true.

3 tests, 3 assertions, 1 failures, 0 errors
```

Ouch!  As is often the case, the code fails on a boundary condition.  Of course, the problem (once identified) is easily fixed by replacing the incorrect operator (<code>></code>) with the correct one (<code>>=</code>).  It's a trivial change, but under what circumstances would we identify this problem in the first place?  Why not call it a day as soon as the first two tests are passing?  We already had [100% test coverage](http://jasonrudolph.com/blog/2008/06/10/a-brief-discussion-of-code-coverage-types "jasonrudolph.com/blog -- A Brief Discussion of Code Coverage Types") [1], and we certainly don't get any extra credit from our coverage analysis tool for adding this new test case.  Geoffrey Wiseman sums up this situation nicely in his [commentary on making effective use of coverage analysis](http://www.ejlife.net/blogs/john/2006/08/16/1155746828758.html#comment1156136055323 "Geoffrey Wiseman's response to 'Testing: Coverage Reports Considered Dangerous'"):

> Coverage [reports] are great at telling you when you don't have enough tests.  They're terrible at telling you that you have enough, that they're good enough, etc.

The standard test-driven development approach serves us well: write a test, watch it fail, and then write the code to make it pass.  But there's a next step as well: we need to ask which tests are still missing.  We need to apply that critical thought.  As soon as we finish writing the first two tests above, we should immediately start looking for the "abusive" tests (as [Eric Sink lovingly refers to them](http://www.ericsink.com/articles/Code_Coverage.html "Advocating the Use of Code Coverage")) that we can write to make our code fail.  Where are the edge cases?  Where are the exception cases?  What should happen if we pass in a negative value?  A nil value?  Our test suite should be specific in its demands of our code.

## Use it wisely

A green test suite and high code coverage only means that we've satisfied the functionality that's *currently* specified by our tests.  We can (and should) rely on the coverage report to spot the code that isn't yet exercised by our test suite, but we can't stop there.  

In [Waltzing with Bears](http://amazon.com/dp/0932633609 "Amazon.com: Waltzing With Bears: Managing Risk on Software Projects: Tom DeMarco, Timothy Lister"), Tom DeMarco and Timothy Lister remind us that "while it's possible to specify a product ambiguously, it is not possible to build a product ambiguously."  The applications we build are always doing *something* in the corner cases.  In the exception cases.  But are they doing the *right* thing.  And without proper tests (i.e., executable specifications), how can we be sure?

----

## Notes

[1] If you recall from our [recent discussion on code coverage types](http://jasonrudolph.com/blog/2008/06/10/a-brief-discussion-of-code-coverage-types "jasonrudolph.com/blog -- A Brief Discussion of Code Coverage Types"), this is the part where you ask, "Exactly what *kind* of coverage are we talking about here?"  Well, despite the fact that rcov only reports line coverage analysis, we can still deduce fairly quickly that this particular code has 100% line coverage, 100% branch coverage, and 100% path coverage.

----

This post is part of the [Testing Anti-patterns series](http://jasonrudolph.com/blog/testing-anti-patterns-how-to-fail-with-100-test-coverage/ "jasonrudolph.com/blog - Testing Anti-patterns"): a series of essays taken from a conference talk titled, [How To Fail With 100% Test Coverage](http://blog.thinkrelevance.com/2008/5/23/how-to-fail-with-100-test-coverage "Relevance Blog : How To Fail With 100% Test Coverage").

--

**Thanks** to [Aaron Bedra](http://aaronbedra.com/ "aaronbedra.com") and [Greg Vaughn](http://gigavolt.net/blog/ "Potential Differences") for reading drafts of this post.
