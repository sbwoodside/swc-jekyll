---
layout: post
title: all I need to know I learned from symbian.com 
---


such as <a href="http://www3.symbian.com/faq.nsf/0/5F141D7F434C508380256A570051BA3A?OpenDocument">what the heck all those different UIDs are for </a>. Here's a quicko primer:<ul><li>The first UID indicates the structure of the file </li><li>The second UID indicates the outermost "interface" provided by the file </li><li>The third UID indicates a particular instance of the object identified by the other two UIDs </li></ul>

So it sounds to me like: uid1=filetype, uid2=resourcetype, uid3=myuid. Or something like that. 

Anyway, for a DLL, I think according to this and other docs I need to have: uid1=KDynamicLibraryUid=0x10000079, then uid2=KSharedLibraryUid=0x1000008d, then uid3=myownUID.
