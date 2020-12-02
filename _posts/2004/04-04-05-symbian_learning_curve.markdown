---
layout: post
title: symbian learning curve 
---


I feel like I may be slowly getting on top of the symbian programming API. One thing you <strong>have </strong>to do is enable the full error codes for leaves and exceptions. There's a SIS file you can download to turn it on (sorry I don't have the link on hand). Then you can look up the <a href="http://www.symbian.com/developer/techlib/papers/errores/Erresapi.html">errors from untrapped leaves </a>and the <a href="http://www.symbian.com/developer/techlib/v70docs/SDL_v7.0/doc_source/reference/SystemPanics/">system panic codes </a>. Oddly, the term "panic" is used for user level application crashes. These would usually I think be more accurately called exception codes. 

Another useful thing I've discovered is the way to grab the current free memory (in bytes). You can do something like this:

<pre>TInt memoryfree; HAL::Get(HALData::EMemoryRAMFree, memoryfree); TBuf&lt;99&gt; msg; msg.Format( _L("Free memory is %d"), memoryfree ); RFileLogger::Write(LOG_DIR, LOG_NAME, LOG_MODE, msg); </pre>

Useful eh? You'll need to include hal.h and hal_data.h and link hal.lib. Note that this is NOT well documented! There is a better documented call that does something similar but it's deprecated. 

I wish the Symbian API had string support that was more ANSI C++ strings, or just char * strings. I haven't really figured out "descriptors" yet (even though I'm using them...).
