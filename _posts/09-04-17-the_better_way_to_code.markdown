---
layout: post
title: The better way to code error-handling routines
---


There's an excellent <a href="http://guides.rubyonrails.org/getting_started.html">guide to Rails 2</a> that I'm reading through right now, but I don't like this bit:

<pre>    <span class="keywords">if</span> <span class="ivar">@comment</span>.save<br />      redirect_to post_comment_url<span class="brackets">(</span><span class="ivar">@post</span>, <span class="ivar">@comment</span><span class="brackets">)</span><br />    <span class="keywords">else</span><br />      render<span class="symbol"> :action</span> =&gt; <span class="string">"new"</span><br />    <span class="keywords">end</span></pre>

It's much better like this:

<pre>    render :action =&gt; "new" and return unless @comment.save<br />    redirect_to post_comment_url(@post, @comment)</pre>

They do exactly the same thing, but mine is 2 lines instead of 5, and mine clearly eliminates the exceptional/error case first, and then leaves you to see the normal case. In fact, I virtually always code this way when I can, deal with the error cases first, and return, and then the rest of the function is an un-nested normal case handler.
