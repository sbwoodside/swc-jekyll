---
layout: post
title: iMovie to ffmpegX to DivX encoding 
---


<a href="http://www.videohelp.com/forum/viewtopic.php?p=834633&amp;highlight=imovie#834633">How to properly use </a>the kick-ass <a href="http://homepage.mac.com/major4/">ffmpegX </a>(for OS X, a wrapper for all kinds of open source tools) to encode your iMovie movies.<blockquote>It is very important, that you do NOT choose the "Full Quality DV" Setting when exporting from iMovie. This just makes iMovie glueing the 2GB chunks together in which it records movies. Mencoder can't handle that. Here's what to do: Choose "Expert settings". Click "Export". Choose "Movie to Quicktime Movie". Click "Options". In "Video Settings" choose "DV PAL" (or NTSC, if you are on that TV System). In the Audio settings, choose uncompressed 48khz Stereo. Uncheck "Prepare for Internet streaming". Make sure the output file has .mov as extender. Now the recording is reencoded as a single movie which Mencoder will encode completely as AVI. </blockquote>
