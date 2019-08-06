---
layout: post
title: unflac.sh - Convert FLAC files into 320 kbps MP3 files
---


Convert FLAC files into 320 kbps MP3 files. Someone might find this useful. I call it unflac.sh. It will take every .flac file in the current directory and convert it to MP3 using lame's "insane" preset (which shows what the lame people think about mp3...)

<pre><br />#!/bin/tcsh<br /><br /># Deal with FLAC, CUE file to convert to high-quality MP3 with LAME<br /><br /># Split a foo.cue / foo.flac combo (e.g. from EAC) into separate flac files<br />####cuebreakpoints *.cue | shnsplit -o flac *.flac<br /><br /># convert flac to MP3<br />foreach f (*.flac)<br />  flac -c -d "$f" | lame --preset insane - "${f}.mp3"<br />end<br /><br /># Re-add the tags to the separate files<br />cuetag.sh *.cue *.mp3</pre>

You'll need to have flac and lame installed. It also tries to restore tags using cue but that doesn't seem to work. So sorry.

Why would I do this? Basically, because:

<ul><li> my MP3 player (N95) doesn't support FLAC </li><li>and doesn't have the room for it anyway</li><li>and iTunes doesn't support FLAC either (stupid apple...)</li></ul>

 Some day when I have a player that does, I'll probably switch to all FLAC, or apple lossless or whatever, but in the meantime 320 MP3s from lame are pretty good. I won't say I can't hear the difference because I haven't tried REALLY HARD, but for the listening I'm doing I can't hear the difference...
