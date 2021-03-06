---
layout: post
title: mobile CSS 
---


I decided to revisit the mobile CSS situation today. It's actually pretty good. <a href="http://www.htmldog.com/ptg/archives/000056.php">HTML Dog </a>has a pretty good update as the to the situation but I'll summarize it for you. 

Basically CSS comes with so-called <code>media </code>types which include <code>all, screen, print, handheld </code>and some others that presently aren't probably worth bothering about. I've already been using the <code>print </code>thing as you can tell if you have a recent browser and you do a print preview of this page. The styling is quite different from the screen version. It's pretty easy to do, just look at the source of this page, you just define a <code>print.css </code>and a <code>screen.css </code>and then, in each one, <code>@include common.css </code>which would contain basic character styling and colours that are used in all the medias. 

So the point here is <code>handheld </code>media type, if supported correctly in the mobile browsers, can be used the same way. Is it supported correctly? Yet? Well, the test page <a href="http://htmldog.com/test/handheld.html">http://htmldog.com/test/handheld.html </a>will tell you - just point your phone browser at it. The CORRECT answer SHOULD be, "no" for the screen ones and "yes" for the handheld ones. 

My Nokia 6630 incorrectly ignores all the styles. My Sony-Ericsson S710a correctly ignores the screen styles and uses the handheld styles. Yay SE. 

Also notice that if you grab the Opera web browser, View menu, Small Screen, you can see the correct result as well. 

So, using that I've set up a few things.<ul><li>Repeat the page title at the top of the page - useful because a lot of phone browsers don't show the full <code>title </code>on the screen </li><li>Hide a lot of the bling, like the banner, the footer - keep from spamming the small screens. I do this by defining <code>div#footer { display: none; } </code>and so on in the handheld.css file </li><li>Add a "Skip navigation" link at the top of the page - add an anchor <code>#contentbox </code>link at the top of the page that only shows up in the mobile version of the page - this is so that people don't always have to scroll down every new page </li></ul>

That's about it for now. My pages are already really lightweight in terms of KBs and I assume the phone browsers don't bother loading images that are hidden by CSS. So the result is an HTML + CSS solution that doesn't require any browser detection, rewriting any of your pages, or server-side junk.
