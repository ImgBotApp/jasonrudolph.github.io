---
title: "Testing anti-patterns: Overspecification"
layout: post
tags:
- testing
- testing anti-patterns
---
Tests increasingly serve multiple roles in today's projects.  They help us design APIs through test-driven development.  They provide confidence that new changes aren't breaking existing functionality.  They offer an executable specification of the application.  But can we ever get to a point where we have too much testing?  

## Enough is enough

Consider the following test that you might come across in an application with a less-than-ideal test suite.  (We'll pick on some badly-written Rails code for this example, but the ideas we'll discuss are certainly not unique to just Rails or Ruby or even just to dynamic languages.  Unfortunately, these problems are quite universal.)

```ruby
require File.dirname(__FILE__) + '/../test_helper'

class ProductsControllerTest < ActionController::TestCase
  def test_something
    product = Product.create(:name => "Frisbee", :price => 5.00)
    get :show, :id => product.id
    assert_response :success
    product = assigns(:product)
    assert_not_nil product
    assert product.valid?
    assert product.name == "Frisbee"
    assert product.price == 5.00
  end
end
```

Whoa!  That sure is a lot going on in a single test case. What exactly is it that we're trying to test here?  Let's take a step back and see if we can figure it out. [1]

* **Line 5** - We start off by creating a new product.  We give the product a name and a price and call <code>#create</code>.  Since we're in a Rails app, without looking elsewhere in the code, we can make an educated guess that <code>Product</code> is an <code>ActiveRecord</code> subclass and that calling <code>#create</code> will persist the product to the database.
* **Line 6** - We send an HTTP GET request to a <code>#show</code> method and pass along the ID of the product we just created.  Since we're in <code>ProductsControllerTest</code>, we can safely infer that we're calling the <code>#show</code> action in the <code>ProductsController</code> class.
* **Line 7** - We assert that the controller action responded with HTTP status code 200 (i.e., success).
* **Lines 8-9** - We look for an object stored in the <code>assigns</code> hash (i.e., the hash of variables that will be available to the view template) with a key of <code>:product</code> and we assert that it's not nil.
* **Line 10** - We verify that the product object satisfies all the product validation rules (though we can't know what those rules are without taking a look at the <code>Product</code> class).
* **Lines 11-12** - We assert that the attribute values we provided when creating the product (in line 5) match the attribute values stored in the object we fetched from the <code>assigns</code> hash.

For a class called <code>ProductsControllerTest</code>, it sure feels like we're doing a fair bit more than just testing the code we'd expect to find in <code>ProductsController</code> (assuming <code>ProductsController</code> conforms to the traditional responsibilities of a controller).  Let's take a look at the controller code to better understand exactly what it is that we're testing.

```ruby
class ProductsController < ApplicationController
  def show
    @product = Product.find(params[:id])
  end
end
```

It turns out that our controller code is notably simpler than our test case would have led us to believe.  The <code>#show</code> action does indeed stick to the expected behavior of a controller, and in this case, it's able to provide that behavior in a single line of code (despite the 8 lines of test code currently employed above).  That single line satisfies all of the expectations of the <code>#show</code> action: look up the product with the given ID and place the product object in an instance variable for use by the view.

If the <code>#show</code> action isn't responsible for knowing how to successfully save a new product record into the database, why does our test case attempt to provide the data for creating a new product?  What will happen to our test case when someone adds a new validation rule requiring that all products also include a quantity attribute?  Unfortunately, the test as it's currently written will break.  And while a failing test is often a welcome warning that our changes have inadvertently broken a part of our application, it's far from desirable for a *model*-level rule related to creating new records to cause a failure in a *controller* test related simply to displaying existing records.  In short, we've given our test case too much responsibility, and in doing so, we've made it fragile.

We can see from the <code>#show</code> action above that not only is the controller not responsible for knowing how to create a valid product, it's also not responsible for ensuring that a product's attributes are properly populated when the record is read from the database.  However, if we take another look at the last few lines of the test case, we might think otherwise.  That brings us to the second problem with this particular test: it's a rotten source of documentation for the code being tested.  As we increasingly move toward tests as *specifications* of our application's behavior, it's vital that those specifications clearly communicate the expected behavior.  As it's currently implemented, the **overspecification** in this test case leaves the reader having to do way too much work to figure out the true expectations of the code being tested.

## Communicate essence

Let's take another pass at writing a test for the <code>#show</code> action, this time with an eye toward removing the fragility of the previous test case and increasing the value of the test as a specification.

```ruby
require File.dirname(__FILE__) + '/../test_helper'

class ProductsControllerTest < ActionController::TestCase
  def test_should_show_product
    product = create_product
    get :show, :id => product.id
    assert_response :success
    assert_equal product, assigns(:product)
  end
end
```

In this implementation, we've abstracted away the logic for creating a new product in line 5.  We've defined a helper method for use by any and all tests in our application that have a need to create a new product.  If and when the rules for successfully creating a new product change, we'll update the <code>#create_product</code> method, and we won't have to touch the code in <code>ProductsController</code> or <code>ProductsControllerTest</code> at all. [2]

As for the four assertions that appeared at the end of our first attempt at this test case, we've replaced those assertions with a single (stronger) assertion.  Where we previously asserted that the <code>assigns</code> hash held a non-nil product, that the product was valid, and that its attributes matched the attributes used at the beginning of the test, we now simply verify that the product object in the <code>assigns</code> hash is equal to the product object that we created at the beginning of the test.  That single line more accurately and more concisely expresses our expectation: that the product whose ID we provide in the request to the <code>#show</code> action is the same object that's made available to the view.  

By focusing our test case on the *essence* of the code under test, we've ended up with less test code to maintain.  And with the extraneous setup and assertions removed, the remaining test code provides a clearer and less fragile specification of the behavior being tested. [3]

## May I take your order, please?

In the previous example, we *might* have detected the overspecification by the significant mismatch between the lines of test code and the lines of production code, or seeing model-specific assertions in a controller-specific test may have caught our eye.  But, overspecification comes in more subtle forms as well.  Consider the following method provided by [<code>ActiveRecord::Base</code>](http://api.rubyonrails.org/classes/ActiveRecord/Base.html#M001329 "Class: ActiveRecord::Base") for fetching the list of columns that hold domain-specific content from a model class in Rails.

```ruby
# Returns an array of column objects where the primary id, all columns ending in "_id" or "_count",
# and columns used for single table inheritance have been removed.
def content_columns
  @content_columns ||= columns.reject { |c| c.primary || c.name =~ /(_id|_count)$/ || c.name == inheritance_column }
end
```

To test this method, we'll need a sample <code>ActiveRecord</code> model class.  Let's use the <code>Topic</code> model, which is backed by the following table.

```ruby
create_table :topics, :force => true do |t|
  t.string   :title
  t.string   :author_name
  t.string   :author_email_address
  t.datetime :written_on
  t.time     :bonus_time
  t.date     :last_read
  t.text     :content
  t.boolean  :approved, :default => true
  t.integer  :replies_count, :default => 0
  t.integer  :parent_id
  t.string   :type
end
```

In our first attempt at testing the <code>#content_columns</code> method, we might come up something similar to this:

```ruby
# (Naive) First Attempt
def test_content_columns
  content_columns      = Topic.content_columns
  content_column_names = content_columns.map {|column| column.name}
  assert_equal %w(title author_name author_email_address written_on bonus_time last_read content approved), content_column_names
end
```

Can you spot the overspecification?  To give you a hint, compare that test to the actual test employed in the <code>ActiveRecord</code> test suite:

```ruby
# The Real Deal
def test_content_columns
  content_columns        = Topic.content_columns
  content_column_names   = content_columns.map {|column| column.name}
  assert_equal 8, content_columns.length
  assert_equal %w(title author_name author_email_address written_on bonus_time last_read content approved).sort, content_column_names.sort
end
```

If you've ever written a test for something that returns an ordered list of items where the actual order either doesn't matter or isn't guaranteed, you've probably been bitten by this breed of overspecification, and there's a good chance your solution matched the solution used in the <code>ActiveRecord</code> test code above.  Because the <code>#content_columns</code> method doesn't guarantee that the columns will be returned in any particular order, it's inappropriate (and fragile) for our test to specify a certain order.  

While the actual <code>ActiveRecord</code> solution above works, it too could be better.  First, since we know that the two arrays in line 6 won't be equal unless they have the same length, we can safely remove the extraneous length assertion in line 5.  Second, when we see the calls to <code>#sort</code> on line 6, we're forced to pause (if even for just a moment) to think about why it might be important to sort the two arrays.  We don't really *want* to sort the arrays; we're just using that technique to get around the fact that order doesn't matter to us, but it does matter when Ruby compares two arrays for equality. Since we really only want to assert that the arrays have the same elements, why not do exactly that?

```ruby
# Don't Make Me Think
def test_content_columns
  content_columns        = Topic.content_columns
  content_column_names   = content_columns.map {|column| column.name}
  assert_same_elements %w(title author_name author_email_address written_on bonus_time last_read content approved), content_column_names
end
```

By using an assertion like [Shoulda's](http://www.thoughtbot.com/projects/shoulda "thoughtbot: Shoulda testing plugin") [<code>assert\_same\_elements</code>](http://dev.thoughtbot.com/shoulda/classes/ThoughtBot/Shoulda/General.html#M000005 "Module: ThoughtBot::Shoulda::General") method, our test can clearly and concisely express the expected behavior.

## Use it wisely

Overspecification comes in many flavors, and the examples above in no way represent a comprehensive list.  As developers, we frequently strive to write as little code as possible to accomplish the task at hand.  When it comes to writing tests, we should very much keep that goal in mind as well.  Good tests communicate the essence of the scenario being tested and nothing more.  While I doubt a project will ever suffer from too much testing, it can certainly suffer from tests that specify too much.

----

## Notes

[1] If this test seems absurd to you, good!  Your ability to detect this type of overspecification will serve you well.

[2] The actual implementation of the <code>#create_product</code> method isn't particularly pertinent in this discussion.  (In the Rails space, there's certainly [no](http://manuals.rubyonrails.com/read/chapter/26 "A Guide to Testing the Rails") [shortage](http://replacefixtures.rubyforge.org/ "FixtureReplacement at RubyForge") [of](http://github.com/thoughtbot/factory_girl "thoughtbot's factory_girl at GitHub") [options](http://www.dcmanges.com/blog/38 "Dan Manges's Blog - Rails: Fixin' Fixtures with Factory").)  

[3] With all the excessive thoroughness that went into overspecifying the the *current* behavior of the <code>#show</code> method, is it possible that we've been too distracted to identify other functionality that's still *missing* from that method?  In the next post, we'll take a look at overspecification's more lethargic cousin: [underspecification](http://jasonrudolph.com/blog/2008/07/08/testing-anti-patterns-underspecification "jasonrudolph.com/blog -- Testing Anti-patterns: Underspecification").

----

This post is part of the [Testing Anti-patterns series](http://jasonrudolph.com/blog/testing-anti-patterns-how-to-fail-with-100-test-coverage/ "jasonrudolph.com/blog - Testing Anti-patterns"): a series of essays taken from a conference talk titled, [How To Fail With 100% Test Coverage](http://blog.thinkrelevance.com/2008/5/23/how-to-fail-with-100-test-coverage "Relevance Blog : How To Fail With 100% Test Coverage").

--

**Thanks** to [Justin Gehtland](http://thinkrelevance.com/about "Justin Gehtland @ thinkrelevance.com"), [Muness Alrubaie](http://muness.blogspot.com/ "Mundane Essays"), and [Glenn Vanderburg](http://vanderburg.org/Blog "Glenn Vanderburg: Blog") for reading drafts of this post.
