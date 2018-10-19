---
layout: post
title: Possible circumvention method for Apple's new iTunes 6 Music Store DRM
---
<div class="floating_right"><img src="/weblog/images/2006/jhymn_icon.png" alt="jhymn icon" /></div>

Apple uses a form of <a href="http://en.wikipedia.org/wiki/Digital_rights_management">DRM </a>with the <a href="http://www.apple.com/itunes/music/">iTunes Music Store </a>. While I love iTMS, I can't stand the DRM. The files come down as <code>.m4p </code>files which are AAC with an Apple DRM system called <a href="http://en.wikipedia.org/wiki/FairPlay">Fairplay </a>. 

Now with iTunes prior to version 6.0 there was a great program called <a href="http://www.hymn-project.org/jhymndoc/">JHymn </a>which would strip the DRM from all your iTMS song automagically. Cool! It was built on reverse-engineering work by <a href="http://www.nanocrew.net/">DVD John </a>and enhanced by other people. Unfortunately, Apple messed around with FairPlay in iTunes 6.0 and JHymn no longer decrypts it. 

But wait -- says I -- I have an old <a href="http://www.apple.com/airportexpress/">Airport Express </a>and it plays my encrypted music just fine! It was made a long time before iTunes 6.0 came out. Is it possible that the music is being transmitted over the WiFi connection unencrypted? 

The AirPort Express contains a little computer that can translate mp3, AAC, and AIFF files into an analog output. I know that it only supports certain formats, because I have audio files in other formats that iTunes will play on my computer but not on my stereo. That means that the Express must contain hardware/software that understands AAC. But it would only understand the old Fairplay, not the new one. 

That means that iTunes 6.0 is taking out the new DRM <strong>before it sends it over the air </strong>to the express. And that means it should be possible to write a program that finds that stream of unencryted data and read it back into an unencrypted AAC.
