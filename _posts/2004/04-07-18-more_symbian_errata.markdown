---
layout: post
title: more symbian errata 
---


I'm now porting my Semacode DLL SDK over to windows so that I can build a WINS (emulator) library and DLL file. Needless to say there are some small hiccups. Here's one. I'm using Visual C++ .NET, which while it apparently works, is not like the standard. They still consider VC6 to be standard I think. So when I get this error:

```
LNK2019: unresolved external symbol __ftol2
```

I'm in a bit of trouble. Fortunately I think I found the solution, which is ugly, but works. Go into the file `C:Symbian6.1SharedEPOC32Toolscl_win.pm` and search for the line that contains "/W4" and change it to this:

```
"CLFLAGS = /nologo /Zp4 /W4 /QIfist"
```

(so basically add /QIfist to the options). So what's the problem. I guess that symbian's tools suck? 

While I'm here, remember that `cls` will clear the scrollback buffer when you are in the fugly DOS shell.
