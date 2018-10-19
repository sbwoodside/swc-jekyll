---
layout: post
title: fun with porting 
---


Today I ported the decoding porting of my <a href="http://semacode.org">semacode </a>application from java to C++. As a part of the process I first went to ANSI C++, using C++ strings and couts to output to the console. Then, I make my own simple character buffer class and eliminated the C++ strings which aren't supported in Symbian. Symbian has it's own system of "descriptors" which are O-O and to my noviciate mind seem horrifyingly complex. So my software spits out its result as a simple char* C string. 

Next I compiled and built the simple "helloworld" example from the nokia series 60 examples pack. It comes with the SDK. At the point where the code inserts the "Hello" literal I replaced it with a call to my decoder (which contains at this stage a test pattern). Then I turn the C-string result into a descriptor. As far as I can tell, there doesn't seem to be any API in symbian that will do this conversion for you (!!) although <a href="http://www.symbian.com/developer/techlib/v70docs/SDL_v7.0/doc_source/DevGuides/cpp/Base/BuffersAndStrings/Descriptors/DescriptorsGuide3/HowToPointersTPtrC.guide.html">this page </a>seems as though maybe it offers some hints. I can't tell. Anyway, a search in google found me <a href="http://forum.newlc.com/viewtopic.php?p=2514&amp;highlight=">this post on NewLC </a>with some code that did the trick. I added my ported code to the helloworld code, installed the result and ran it and got a nice URL output on the screen.
