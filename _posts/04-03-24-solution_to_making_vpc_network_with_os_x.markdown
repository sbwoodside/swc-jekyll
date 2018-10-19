---
layout: post
title: Solution to making VPC network with OS X 
---


I found a solution to my <a href="http://simonwoodside.com/weblog/2004/03/23">long-standing VPC problem </a>today. The trick was to add "airport" to my google queries. That quickly turned up <a href="http://www.macosxhints.com/article.php?story=20031101210620201">this useful posting </a>on macosxhints. It's a little bit complicated. You have to remember to go into VPC preferences and specify "built-in ethernet" for the network connection. For me, it's worked perfectly for both Windows 2000 and Linux (debian). I run smbd on linux, mount_smbfs the share onto the mac side, load up an XCode project for my symbian development projects, open an SSH window into the debian virtual machine to run 'make' and I'm all set with an environment that's almost like having everything on the mac.
