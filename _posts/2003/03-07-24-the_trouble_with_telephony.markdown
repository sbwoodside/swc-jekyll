---
layout: post
title: The trouble with telephony 
---


I might as well have called this entry voice chat != IP telephony. I've been think about Voice over IP for a while now and reflecting that the IP telephony people are kind of wandering around in the giggly weeds because they keep taking about crazy things like sending DTMF tones over the internet, and needing special hardware and all kinds of crazy stuff that totally goes against the e2e (end-to-end) principles of the internet. I mean, why bother with all that when you can just set up an e2e connection between two computers and start talking? Finally I got the answer, which is that internet telephony people are not talking about voice chat, they are talking about telephones. 

Whoa, slow down. Telephones are not a best effort network, they are a guaranteed service network. The internet, if you use it, will try its best to do what you want but if it can't, hey, too bad buddy. That's a fundamental operating assumption, you can't change that without changing the nature of the internet. If you want to build a guaranteed-service network over top of the internet you're going to have a lot of trouble, because the internet is build up and down on best-effort systems – like ethernet for example. 

So I think that when people talk about "Voice over IP" they need to be really clear about whether they mean a best-effort system or a telephone-like system. Some people seem to think that VoIP should keep working if the power fails. And so on, there's a lot of assumptions built in when you talk about telephony. The other side of the coin would be something more like a voice chat, where you are able to talk to someone anywhere at any time on the internet, but it's just like any other internet services, so you can expect there to be glitches. That's a fundamental part of best-effort networking, and it's also part of why it's so efficient and inexpensive. 

So can VoIP be done over the internet without all kinds of crazy hacks to make it act more like the telephone system? I think so. The codecs are finally here to do reasonable voice quality over a modem connection, using <a href="http://www.speex.org/">Speex </a>. IPv6 will hopefully help us get around the NAT barrier.
