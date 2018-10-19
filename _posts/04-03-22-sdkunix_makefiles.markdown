---
layout: post
title: sdk2unix makefiles
---


I think I'm travelling relatively untrodden turf with <a href="http://simonwoodside.com/weblog/2004/03/07">sdk2unix </a>. So here's another thing I got hung up on and figured out. Probably someone with more makefile experience than I have would have got this instantly, but under OBJECTS you have to have applicationname.o FIRST or else it might not work. That's because the way it's set up, that particular rule will fire off the creation of the .rsg file which is some kind of generated resource file your source code needs or it won't build.
