---
layout: post
title: Getting a "Secure Rip" (a perfect/high-quality mp3 rip of a CD) on a Mac
---


I've been trying to figure out how to get a perfect CD rip on my mac. The problem in a nutshell is that ripping CDs is "unreliable", in other words, it is impossible to be sure when you rip a CD that you have the correct digital data. How good a copy you get depends on your drive and the software you use.

Why care? In the most extreme cases you can literally get blips and pops in your MP3 file. This might occur even with a totally unscratched disc. But more likely you will get a subtle degradation of quality which will be noticeable if you have a good sound system, and that sucks. So.

The gold standard in secure ripping is <a href="http://www.exactaudiocopy.de/">Exact Audio Copy</a>, a Windows-only program and likely to stay that way forever. Why? Because you can run it in boot camp or Parallels or whatever. If you want to use EAC definitely follow a how-to guide such as <a href="http://www.teqnilogik.com/tutorials/eac.shtml">Exact Audio Copy Guide</a>. EAC does not come preconfigured properly.

If you must use a Mac-native program, check out <a href="http://sbooth.org/Max/">Max</a>, and have look online in how to set it up for maximum secure mode, because it doesn't come in that mode by default. Max was originally written more as a transcoding program (converting between formats) but now supports a linux-originating cd ripper called cdparanoia. Audiophiles still prefer EAC to cdparanoia, and I'm not going to tell them they're wrong, even though they are occasionally insane and overly conservative, so I would say stick with EAC.

Oh yeah, and I would also say, rip into FLAC format. Then, use something like Max to convert from FLAC to MP3 320 Kbps (using LAME "insane" mode) for import into iTunes, use on your ipod/phone/mp3 player, etc. In practise it's unlikely you will be able to hear the difference between a lossless format and a 320 mp3. If you REALLY need to you can use Apple Lossless until Apple supports FLAC, but I like FLAC better as it's the open standard and everyone uses it. Archive the FLAC files for the future. You get to keep a perfect copy but not waste GBs of space on your mobile device.

And by the way, if you download music from BitTorrent, you might as well get FLACs, and they are almost always ripped with EAC.

<em>UPDATE: Actually <a href="http://tmkk.hp.infoseek.co.jp/xld/index_e.html">X Lossless Decoder</a> looks like a good replacement for Max. It has the added ability to split a single huge FLAC/CUE combination into multiple MP3s (or any other format) automatically. Just drag the .cue file onto XLD and you're away.</em>
