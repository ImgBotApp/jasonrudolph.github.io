---
title: Evan Phoenix on testing private methods in Ruby
layout: post
tags:
- ruby
- testing
redirect_from: /blog/2007/11/03/evan-phoenix-on-testing-private-methods-in-ruby/
---
At RubyConf today, [Stuart Halloway's Refactotum workshop](http://relevancellc.com/2007/11/2/rubyconf-slides) led to a brief but excellent discussion on the various approaches for testing private methods in Ruby.  Ideas ranged from the typical solution of using <code>#send</code> ([which won't work once Ruby 1.9 lands](http://eigenclass.org/hiki.rb?Changes+in+Ruby+1.9#l23 "eigenclass - Changes in Ruby 1.9")) to [Ryan Davis](http://zenspider.com/RWD/)'s technique of simply making everything public.  [Evan Phoenix](http://blog.fallingsnow.net/), on the other hand, suggested a solution that *avoids* the soon-to-be-brokeness of using <code>#send</code> while still allowing you to benefit from the inherent *intent* expressed by defining a method as <code>private</code>.

To demonstrate, let's assume we have the following (admittedly contrived) [class](http://askaninja.com/ "Ask a Ninja"):

<pre lang="ruby">
class Ninja
  private
    def kill(num_victims)
      "#{num_victims} victims are no longer with us."
    end
end
</pre>         

So how can we make sure that the private method is doing what we want, and do so while testing it in isolation?  Why not temporarily define a new *public* method that simply passes through to our elusive private method?

<pre lang="ruby">
require 'test/unit'

class NinjaTest < Test::Unit::TestCase
  def test_should_punish_sloppy_coders
    @ninja = Ninja.new
    def @ninja.flog_publicly(*args)
      kill(*args)
    end
    assert_equal '3 victims are no longer with us.', @ninja.flog_publicly(3)
  end
end
</pre>                         

Sweet!

<pre lang="text">
$ ruby ninja.rb
Loaded suite ninja
Started
.
Finished in 0.000274 seconds.

1 tests, 1 assertions, 0 failures, 0 errors
</pre>
