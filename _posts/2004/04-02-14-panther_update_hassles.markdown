---
layout: post
title: panther update hassles 
---


I upgraded to Panther (OS X 10.3) a week or so ago and I started having troubles with my development environment. Not so much XCode, that seemed to be working fine. But I coulnd't get AxKit to work. And mozilla / camino to build (but that might be another story). So anyway I'm trying to build AxKit and getting horrible error spews when I try to install the XML::LibXML perl module. I try to debug it and I find there's just too many versions of libxml installed. I can't figure out which one it's trying to use. So after pruning out some versions, that didn't help, things seemed even worse. Finally I decided to nuke my entire fink installation. Someone said that fink gave problems when upgrading to panther. 

Then I reboot my machine and it won't reboot. It hangs at a seemingly random place in the boot process. So I finally did what I should have done at first, which is forget about the "upgrade install" and just wipe out my old system and do a clean panther installation. I can do that, because I keep my home directory on a different partition. I simply create a symlink to it on the root partition. Works like a charm. 

Now I'm reconstructing my system again. Hopefully this time it will work better.
