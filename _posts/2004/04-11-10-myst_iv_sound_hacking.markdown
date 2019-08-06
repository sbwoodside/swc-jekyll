---
layout: post
title: Myst IV sound hacking 
---


I just downloaded the <a href="http://www.mystrevelation.com/">Myst IV Revelation </a>demo (it's free there) and it's very cool. It brings back memories of Myst and maybe (I can hope) it will be as good as Riven was. Anyway, I guess I'm going to buy it as soon as I'm done writing this, but first, some obligatory info on hacking the sound files out of the demo. 

We're talking about the OS X version here, presumably the PC version is analogous. Go into the .app package and look for sound/data. Ignore the .snd files, they are metadata. Inside "data" you will see files with three different extensions. Here's my guide to what they are.<ul><li>.LS0 - inside the "English" folder - these are easy, they are straight OGG vorbis, just rename them with the .ogg extension and play in your favorite player. </li><li>.SS0 - music and some backgrounds. Three of these are straight OGG vorbis files, rename as above. Some of them are ADPCM - see below. </li><li>.SB0 - many of these are 44100 Hz, 2 channel (stereo), 4-Bit 4:1 IMA DVI ADPCM files (a common format in WAV/wave files). You can listen to them using <a href="http://www.soundhack.com/freeware.php">SoundHack </a>a free program for OS X and there's probably similar soft for PCs. Open as unknown format. Set the format to the above. Save Info. Save as. The resulting file should be listenable. NB: Many of these files contain multiple sounds. NB2: Some of them won't work using this technique, I don't know why. </li></ul>

Have fun. 

Update: <a href="http://homepage.mac.com/rshayter/Revelator.html">Revelator </a>will extract just the ogg files automatically. 

PS: Why all the work? They're probably just trying to make it difficult to extract the audio by stripping the normal headers from these files. They could have left the WAV headers in place and made it a lot easier.
