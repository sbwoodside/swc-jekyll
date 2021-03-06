---
layout: post
title: What happens when you don't understand open source licenses?
---


I was just checking out a TextMate-like editor for Windows called <a href="http://e-texteditor.com/">E Text Editor</a>. It looks pretty good, but I was a bit surprised when I read about his "Open Company License".

To be clear, this is something he came up with himself, and it's not a bad idea. To be double clear, it's NOT open source. And he says that up front. <a href="http://e-texteditor.com/blog/2009/releasing-the-source">He added "just one" clause to the standard BSD license</a>:

<blockquote>

Any redistribution, in whole or in part, must retain full licensing functionality, without any attempt to change, obscure or in other ways circumvent its intent.

</blockquote>

Not bad. Users gain because they can modify the software and use the modified version all they want for in house purposes, and they don't have to share those changes with anyone. But they still have to pay him, and that's why it's not open source.

Unfortunately for him, he made a little mistake, because the clause only stipulates on redistribution.

So if you want E Text Editor for free, just download the source, modify it to remove the licensing code, build and use it. As long as you use it only yourself, you're perfectly legit and don't have to pay.

In addition, he left open a rather major hole. Anyone can now make a completely separate small program which downloads the source code, automatically applies a patch which removes the licensing code, builds it and installs on the local computer. This is the way in which many applications include GPL software into non-free, just in reverse. To be clear, my hypothetical program does this:

<ol><li>You download my program, FreeE and run it on your computer.</li><li>FreeE goes online and grabs the source code for E Text Editor.</li><li>FreeE applies a patch to remove the code that makes you pay.</li><li>FreeE builds -- on your local machine -- a new copy of E Text Editor without the pay code.</li><li>FreeE quits and you delete it.</li></ol>

As long as you never distribute your copy of E Text Editor that you get this way, you're totally clear and legally able to use it without paying.

Alexander Stigsen, the author of E, might want to consider changing his license. But even if he does so, the versions he released under the current license will always have this hole. So go ahead, get some free as-in-beer software :-)
