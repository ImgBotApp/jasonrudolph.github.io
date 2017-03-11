---
title: "Testing anti-patterns: The ugly mirror"
layout: post
tags:
- testing
- testing anti-patterns
---
When you're able to write a test, nay, a spec, that not only verifies your code's functionality, but also clearly communicates its intent, you've got a real win on your hands.  It's a win when you're first writing out your test cases as you're TDD'ing your way to the solution.  It's a win to the person providing the peer review of your code.  It's a win for you (again) when you have to revisit (and relearn) the code six weeks from now.  And it's a win for the guy that has to touch this code yet again when you're long gone.  [1]  But when you occasionally find yourself staring at a spec that looks exactly like the code under test, there's surprisingly little *win* left to enjoy.  

Consider, for example, the following Ruby Struct tasked with building a friendly string representation of a user's name and e-mail address.

```ruby
User = Struct.new(:first_name, :last_name, :email) do
  def to_s
    "#{last_name}, #{first_name} <#{email}>"
  end
end
```

I ran across code similar to this example during a recent code review, and when I got to the corresponding test ...

```ruby
require "test/unit"

class UserTest < Test::Unit::TestCase
  def test_to_s_includes_name_and_email
    user = User.new("John", "Smith", "jsmith@example.com")
    assert_equal "#{user.last_name}, #{user.first_name} <#{user.email}>", user.to_s
  end  
end
```

... I couldn't help but feel like I was staring right back at the very code that was supposedly being tested.

[![Ahhhhhhhh!](/resources/20080729-ugly-mirror.jpg "Image courtesy of Pablo Baslini (flickr.com/98621082@N00)")](http://www.flickr.com/photos/98621082@N00/434585853/ "Image courtesy of Pablo Baslini (flickr.com/98621082@N00)") [2]

This **ugly mirror** of the production code leaves much to be desired.  Sure, thanks to the name of the test, we get the general idea that <code>to_s</code> will output some combination of the user's name and e-mail address.  But when we look at the assertion on line 6, we're forced to mentally reverse engineer the code in order to see through to the underlying requirement.  When it comes to quickly and clearly communicating the intent of the underlying code, this test falls far short of its potential.  As it's implemented above, we're probably better off reviewing the production code itself than bothering to look at the test at all.

Of course, it doesn't have to be this way, but it's not unusual to stumble across this kind of test.  In fact, it's remarkably common to see this kind of test when the test is written *after* the production code is implemented.  It's as if once a developer has written the code to perform a task, the guts of the code can't be unseen, and as a consequence, the tests often end up reflecting those inner workings instead of the desired end result.

## No mental juggling necessary

On the other hand, when we're developing test-first, we start out with the end-user requirements in mind, and it's easy to make sure our tests communicate those requirements.

```ruby
require "test/unit"

class UserTest < Test::Unit::TestCase
  def test_to_s_includes_name_and_email
    user = User.new("John", "Smith", "jsmith@example.com")
    assert_equal "Smith, John <jsmith@example.com>", user.to_s
  end  
end
```

When we improve the test to focus on the end result, we can look at the test and instantly see the requirements (and so can all the people that will live with our code long into the future).  Instead of reflecting the ingredients, the test now reflects the end product.  And this allows us to have greater confidence that our code is doing the right thing as well.

Whether it's strings, dates, timestamps, or numeric calculations, [any time we can assert on a literal value, our test will be better off because of it](http://blog.jayfields.com/2008/02/testing-expect-literals.html "Jay Fields' Thoughts: Testing: Expect literals"). [3]  The less logic that's in our assertion, the fewer chances we have for that logic to be wrong, and the less logic we have to dig through to grok what's being tested in the first place.

----

## Notes

[1] And if you're writing a library or framework, the tests may be a win for the users (or potential users) of your code as well.  My colleague [Muness Alrubaie](http://muness.blogspot.com "Mundane Essays") is often seen skipping right over the docs and heading straight for the tests when he wants to check out some new open source code.  (After all, assuming they pass, the tests don't lie.)  And if there are no tests, or if the tests fail to cleanly express the underlying functionality, you can rest assured that he won't be looking at that project for long.

[2] Image courtesy of Pablo Baslini ([flickr.com/98621082@N00](http://www.flickr.com/98621082@N00 "Flickr: Pablo Baslini's Photostream"))

----

This post is part of the [Testing Anti-patterns series](http://jasonrudolph.com/blog/testing-anti-patterns-how-to-fail-with-100-test-coverage/ "jasonrudolph.com/blog - Testing Anti-patterns"): a series of essays taken from a conference talk titled, [How To Fail With 100% Test Coverage](http://blog.thinkrelevance.com/2008/5/23/how-to-fail-with-100-test-coverage "Relevance Blog : How To Fail With 100% Test Coverage").

--

**Thanks** to [Greg Vaughn](http://gigavolt.net/blog/ "Potential Differences") for reading drafts of this post.
