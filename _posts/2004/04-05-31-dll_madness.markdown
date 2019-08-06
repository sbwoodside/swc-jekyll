---
layout: post
title: dll madness 
---


I'm still trying to figure out how to build a DLL for symbian on Linux. sdk2unix didn't do it "out of the box" so I'm learning, learning, learning about how DLLs work, how symbian builds DLLs, etc. Here's one: if you include a DLL's lib stub file in your makefile, it still won't link to the .app unless you actually use something from the DLL in your source code.
