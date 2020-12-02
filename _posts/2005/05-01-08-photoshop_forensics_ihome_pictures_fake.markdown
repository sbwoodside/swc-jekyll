---
layout: post
title: 'photoshop forensics: iHome pictures fake'
---


In response to <a href="/weblog/2005/01/07">my post </a>Rui <a href="http://the.taoofmac.com/space/blog/2005-01-07.23%3A48">noted </a>some pics of what purports to be an Apple 'iHome'. The photos aren't photoshopped, but it looks to me like a mock up. I did some "forensic analysis" in photoshop (I've been doing a lot of image processing lately). 

I used photoshop's edge-detection convolution code to locate any strong/fast colour gradients in the image. This is a good way to find hard-to-see features.

<div class="floating_left"><img src="/weblog/images/2005/ihome-3a.png" alt="ihome" /><br /><img src="/weblog/images/2005/ihome-3b.png" alt="ihome" /></div>

This first big clue showed up using Find Edges and Levels. There's an extra horizontal line on the back of the box between what should be the top edge and the apple logo. 

Also what are those vertical lines that run across the ports? They look a bit like the lines that appear in transparent shrink-wrap packaging.

<div style="clear: both;"></div>

<div class="floating_left"><img src="/weblog/images/2005/ihome-1a.png" alt="ihome" /><br /><img src="/weblog/images/2005/ihome-1b.png" alt="ihome" /></div>

This image of the front of the box shows what appear to be the edges of a card or inserted sheet of paper under a plastic wrap. 

Plastic wrap might also explain the rainbow line effect that is visible across the dvd slot. Due to thin-film interference (diffraction). 

For the next images I used Levels and Hue/Saturation. The blocking comes from JPEG.

<div style="clear: both;"></div>

<div class="floating_left"><img src="/weblog/images/2005/ihome-1c.png" alt="ihome" /><br /><img src="/weblog/images/2005/ihome-1d.png" alt="ihome" /></div>

Home run. There's a tell-tale colour transition on both sides between the card and the background material. The card shows up more brownish in the top pic, the background/box material as purple-ish. This indicates two different kinds of material.

<div style="clear: both;"></div>
