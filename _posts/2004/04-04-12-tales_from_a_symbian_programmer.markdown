---
layout: post
title: tales from a symbian programmer 
---


Now that I've got my semacode app marginally working. I say working, because it <b>does </b>actually work. You can click on a symbol (I mean, photo a barcode), and it will take out the URL and then you can launch the URL in the browser. It's slow and ugly but it works. 

Anyway, now I figure I can call myself a symbian programmer. I would say that I have officially figured out strings management. I even think I've done a clever thing or two with descriptors. The whole idea that there's a class called HBufC -- for "Heap Buffer Const" -- is a little silly. Especially because you can obtain modify access to the contents so it's actually not const after all. 

As for the UI model, I kind of generally grok how it works but I wouldn't trust myself to make big changes yet. I'm working off some example code that already does basically what I need so I want to keep the UI changes VERY minimal. But towards prettying up the app a bit I need to figure out how to change the icons (my attempts so far, abortive). And I'll probably have to create some kind of form field or something to give some instructions to the user. Well, the less UI work the better! 

I just talked to some folk on the #mobitopia channel today and they said that the most popular symbian smartphones by far are the nokia models. 3650, and 6600 basically. I was somewhat relieved to learn that the P800 and P900 aren't so popular. That good, because it probably means that demands for a UIQ port won't be so strong. I don't think a UIQ port would be super hard, but I'd have to get a new (expensive) phone and mess around with a new UI API. 

I've got some marginally useful logging code that I'll provide at some point since it might be useful to someone. I use heavy duty logging because well, there's no debugger on the device.
