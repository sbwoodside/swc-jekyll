---
layout: post
title: sdk2unix for symbian on linux
---


After a week of messing around with windoze and linux toolkits, I finally did a successful build and run of an example app on my nokia 3650 using Symbian C++. Was it any of the toolkits I've already mentioned that I used? No, it was <a href="http://www.ki-ag.de/pages/tech/SYMBIAN-SDK-on-unix.html">sdk2unix </a>, a seemingly wonderful (hey it works!) distro by <a href="http://www.koeniglich.de/">Rudolf Koenig </a>and distributed at the <a href="http://www.ki-ag.de/index.html">Knowledge-Intelligence AG </a>site (some kind of german company). They've got howto's for a bunch of symbian platforms, but note in particular the <a href="http://www.ki-ag.de/pages/tech/SymbianSDK/symbian_sdk_6.1_on_linux.html">Series60 (SymbianOS 6.1) SDK on Linux/Unix HOWTO </a>which is what I followed. 

In addition to what they say there I would add the following notes:<ul><li>It worked for me with the 1.2 nokia SDK (it's not clear that when the howto was written 0.9 was the latest) </li><li>when you run bin/install_gcc539 you must give absolute paths </li><li>target-directory is the same directory for both bin/install_gcc539 and bin/install_series60_sdk </li><li>you will have some minor troubles with case-sensitive names ... I just renamed directories that were expecting something different. </li></ul>

I had to do some hacking a little bit to make it all work .... I can't remember everything I did right now. I used <a href="http://www.cdavies.org/permalink/unpackingthenokiaseriessdkonlinux.php">Chris Davies'unpack-s60cppsdk </a>to unpack the nokia SDK under linux. I found that when I went to 'make'in the series60ex/form example I had to fix the case of the include files in a bunch of .cpp files. (i.e., make them lowercase). 

Overall I am VERY happy right now because this makefile system actually makes some sense. The bldmake and makmake and abld crap from symbian is just crap. So, hopefully this success with the example will be followed by me successfully writing my own little hello world program soon! :-)
