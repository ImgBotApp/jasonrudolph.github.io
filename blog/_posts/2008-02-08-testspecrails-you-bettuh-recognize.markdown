---
title: test/spec/rails => You bettuh recognize
layout: post
tags:
- rails
- ruby
- testing
---

Believe it or not, there are still at least [a few](http://robsanheim.com/2008/01/25/why-i-use-testspec-over-rspec/ "Panasonic Youth - Why I use test/spec over rspec") [of us](http://matthewbass.com/2008/01/09/add-layout-checking-to-test_spec_rails-plugin/ "Matthew Bass - Add layout checking to test_spec_on_rails") [crazy hold-outs](http://streamlinedframework.org/articles/2007/12/21/streamlined-goes-test-spec "Streamlined goes test/spec") that still haven't imbibed the increasingly ubiquitous RSpec Kool-Aid.  And for the folks in this crowd that still want BDD-style testing, it's [test-spec](http://chneukirchen.org/blog/archive/2007/01/announcing-test-spec-0-3-a-bdd-interface-for-test-unit.html "Christian Neukirchen: Announcing test/spec 0.3, a BDD interface for Test::Unit") and [test/spec/rails](http://agilewebdevelopment.com/plugins/test_spec_on_rails "Test Spec on Rails") all the way.  So when I recently needed a means for validating that a nontrivial route landed in the right controller/action, I naturally went looking for the test/spec/rails equivalent of `#assert_recognizes`.  When I saw that it was nowhere to be found, I knew I'd found another task for [Open Source Fridays](http://thinkrelevance.com/open-source "Open Source at Relevance") (er, the first half hour of an Open Source Friday).  And thanks to [Matthew Bass](http://matthewbass.com/2008/01/10/layout-assertion-added-to-test_spec_rails/ "Matthew Bass - test/spec/rails committer")'s uncanny responsiveness in applying the patch that [Rob Sanheim](http://robsanheim.com) and I submitted, test/spec/rails now offers some handy new specs for testing your routes.

## `assert_generates` => `should.route_to`

Where you'd use [`#assert_generates`](http://api.rubyonrails.org/classes/ActionController/Assertions/RoutingAssertions.html#M000367 "rdoc - Module: ActionController::Assertions::RoutingAssertions#assert_generates") in traditional Rails + test/unit, test/spec/rails now supports [`#route_to`](http://svn.techno-weenie.net/projects/plugins/test_spec_on_rails/lib/test/spec/rails/should_route.rb "test/spec/rails source code + rdoc -- lib/test/spec/rails/should_route.rb") as a more spec-flavored alternative.  For example, to verify that a given set of URL options routes to the expected path...

```ruby
assert_generates "/users/1", :controller => "users", :action => "show", :id  => "1"
```

becomes

```ruby
{:controller => "users", :action => "show", :id  => "1"}.should.route_to "/users/1"
```

## `assert_recognizes` => `should.route_from`

And where our ancestors once used [`#assert_recognizes`](http://api.rubyonrails.org/classes/ActionController/Assertions/RoutingAssertions.html#M000366 "rdoc - Module: ActionController::Assertions::RoutingAssertions#assert_recognizes"), test/spec/rails now offers <del>`#you_bettuh_recognize`</del> [`#route_from`](http://svn.techno-weenie.net/projects/plugins/test_spec_on_rails/lib/test/spec/rails/should_route.rb "test/spec/rails source code + rdoc -- lib/test/spec/rails/should_route.rb").  "An example would be nice", you say?  Well, to perform essentially the inverse of the above test...

```ruby
assert_recognizes({:controller => "users", :action => "show", :id => "1"}, {:path => "/users/1", :method => :get})
```

becomes

```ruby
{:path => "/users/1", :method => :get}.should.route_from :controller => "users", :action => "show", :id =>"1"
```

The [rdoc](http://svn.techno-weenie.net/projects/plugins/test_spec_on_rails/lib/test/spec/rails/should_route.rb "test/spec/rails source code + rdoc -- lib/test/spec/rails/should_route.rb") offers additional examples, and check out the [test/spec/rails README](http://svn.techno-weenie.net/projects/plugins/test_spec_on_rails/README "test/spec/rails README file") for more mappings from old-school test/unit assertions to test/spec/rails equivalents.
