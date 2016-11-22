---
layout: post
title: How to decompile and obfuscate in MIDP on OS X 
---
<p>OK, just some notes. To decompile any java jar, use something like this: </p><pre>javap -c -classpath ./semacoderead.jar org.semacode.imagerec.Ecc200Decoder </pre><p>I'm using <a href="http://www.mpowerplayer.com/">mpowerplayer </a>on OS X to do my J2ME compiling, which makes things pretty easy, except that I want to use the <a href="http://proguard.sourceforge.net/">ProGuard </a>obfuscator. Obviously! You NEED to obfuscate if you've got code like mine (for semacode) that needs to be protected from reverse engineering which is SUPER easy with java. It's available from fink. </p>
