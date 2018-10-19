---
layout: post
title: How to make an iPhone button highlight (hold state)
---


Here's how to use iPhone SDK to make a button hold it's on/highlighted state when you click on it:

<pre>- (IBAction)badButton:sender; {<br />&#160; badButton.highlighted = YES;<br />&nbsp; if( _hasChosen == NO ) {<br />&nbsp;&nbsp;&nbsp; _hasChosen = YES;<br />&nbsp;&nbsp;&nbsp; [NSTimer scheduledTimerWithTimeInterval:0.0 target:self selector:@selector(badButton:) userInfo:nil repeats:NO];<br />&nbsp; }<br />}</pre>

On simulator it looks perfect, but on device there's a brief moment when it goes white before it goes blue/highlighted again.
