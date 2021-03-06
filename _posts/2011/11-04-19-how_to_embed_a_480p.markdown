---
layout: post
title: How to embed a 480p YouTube video
---


Google doesn't provide any "official" way to embed a YouTube video in 480p. It always drops you down to 360p by default, and that just looks crap. You can embed in HD so why not 480p? No one knows. But don't despair, there is a way!

Here's some code for you:

<pre>&lt;object width="853" height="505"&gt;
  &lt;param value="http://www.youtube.com/v/MOVIE_ID&amp;amp;hl=en_US&amp;amp;fs=1&amp;amp;rel=0" name="movie"&gt;
  &lt;param value="true" name="allowFullScreen"&gt;
  &lt;param value="always" name="allowscriptaccess"&gt;
  &lt;embed width="853" height="505" allowfullscreen="true"
    allowscriptaccess="always"
    type="application/x-shockwave-flash"
    src="http://www.youtube.com/v/MOVIE_ID&amp;amp;hl=en_US&amp;amp;fs=1&amp;amp;rel=0"&gt;
&lt;/object&gt;</pre>

That will give you an "HD width" 480p video. Just change "MOVIE_ID" to the ID of your video (e.g. "J-lHxxToCfo") in both places. The width of the embed will be 853px, which is 16:9 for HD video.

What if your video is 4:3, i.e. 640x480? I can't find any clean way to embed at exactly that size, if you use the above code you'll get black bars on either side. However you can use a negative margin to get a box of the right shape. Just wrap your object like this:

<pre>&lt;div style="width: 640px; overflow: hidden;"&gt;
  &lt;div style="margin-left: -107px;"&gt;
    &lt;object etc ... &gt;&lt;/object&gt;
  &lt;/div&gt;
&lt;/div&gt;</pre>

The controls will go off the screen but at least the user will still be able to click the centre of the video to start and stop it. Here's an example:

<div style="width: 640px; overflow: hidden; z-index: 999;"><div style="margin-left: -107px;"><object height="505" width="853">
  <param name="movie" value="http://www.youtube.com/v/J-lHxxToCfo&amp;hl=en_US&amp;fs=1&amp;rel=0" />
  <param name="allowFullScreen" value="true" />
  <param name="allowscriptaccess" value="always" />
  <embed src="http://www.youtube.com/v/J-lHxxToCfo&amp;hl=en_US&amp;fs=1&amp;rel=0" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" height="505" width="853" /></object></div></div>

My column width is less than 640px but hopefully you get the idea.
