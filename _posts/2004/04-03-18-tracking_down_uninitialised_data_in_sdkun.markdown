---
layout: post
title: tracking down uninitialised data in sdk2unix
---


If you're writing symbian C++ code you might get an error like this from petran:

<pre>ERROR: Dll 'MENUITEMS[10008AD0].APP'has uninitialised data. </pre>

<a href="http://www.symbian.com/developer/techlib/v70docs/SDL_v7.0/doc_source/DevGuides/EssentialIdioms/StaticData.html">this page </a>has a somewhat-adequate description of the problem, but you really should google for "bss segment" to find out what they're talking about. Since you can't build for symbian with this stuff in your code, you need to find and fix it. But the problem is, the error doesn't actually tell you what the offending code is. There's some stuff about .map files but they admit it won't show everything. Well I'll tell you what to do. 

First off, you're looking either for an non-const global variable with no initialization e.g., <code>int foo; </code>or for a static local variable in a function. Now using <a href="http://simonwoodside.com/weblog/2004/03/07">sdk2unix </a>add the following to your CFLAGS in the makefile: <code>-save-temps </code>This is the gcc flag that will save all of the intermediate files as it builds. Included is the .s files which I think are assembly language. grep these files for "bss"

<pre>grep -i "bss" *.s </pre>

If you see one, less or more the file and have a look at what comes after the .bss directive. A few lines down should be the name of the offending variable. 

If you're getting "has initialised data" the solution is probably similar but you need to look for the data segment.
