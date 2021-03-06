---
layout: post
title: How to do rails tests when running with restful_authentication
---


The Restful Authentication plugin seems to be the standard right now, although I'm staring to wish I'd tried something else, maybe AuthLogic... because restful_authentication is kind of poorly documented. One serious error of ommission is how the hell do you update your tests so that you can run them on controllers that require a logged in user? Well, I have had the pain, and so you can have the quick answer, here it is.

Assuming you are using ActionController::TestCase ... first edit test_helper.rb:

<pre>  # Add this helper function to test_helper.rb<br />  # It will allow you to run any block under the aegis of<br />  # a controller of your choosing. This is not something <br />  # that is possibly by default<br />  def run_with_controller( controller_class )<br />    old_controller = @controller<br />    @controller = controller_class.new<br />    yield<br />    @controller = old_controller<br />  end</pre>

Now you can use that helper method in your test cases, in the setup function do this:

<pre>  def setup<br />    run_with_controller(SessionsController) do<br />      post :create, { :login =&gt; "george", :password =&gt; "monkey" }<br />    end<br />  end<br /></pre>

What you're doing here is simply making a POST to the Restful Authentication SessionsController to "create" a new session, pass in a login/password that exists in your fixtures. And that's it.

By the way, if you chose to install with RSpec because of the dire warnings that old fashioned tests will be out of date, but aren't currently using RSpec for you other tests, you should copy the rspec fixture data into test/ so that you get the right password hashes. Tricky...
