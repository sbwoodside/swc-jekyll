---
layout: post
title: My magic box 
---


I just read <a href="http://www.slackwerks.com/the-crew/arete/soekris/soekris.html">Soekris Router Project </a>. Soekris in case you haven't probably heard of it is a little company that makes these fantastic little PC-compatible chipsets that are totally solid-state, no moving parts, DC power, just the basics, a couple of ethernet ports, a PC card slot or two, a CompactFlash slot for the media, and a nifty-looking box. 

And I am very impressed. I can get a <a href="http://www.soekris.com/">Soekris </a>, <a href="http://www.soekris.com/net4511.htm">net4511 </a>, for about $170, and a <a href="http://www.soekris.com/vpn1201.htm">vpn1201 </a>for about $70 and a CF card for about $50, all told, $300 for the hardware and it comes with a <a href="http://www.soekris.com/Pictures/new_case_front.jpg">nifty looking box </a>( <a href="http://www.soekris.com/Pictures/new_case_rearinside.jpg">inside </a>) from Soekris. This is going to be with an extra twist from me because I want to install 6to4 support. I'll tell you why in a minute ;-) 

OK, so first of all this slackwerks HOWTO is going to get me up and running with a totally secure IPSec based WiFi network. That's just cool. Instead of all this WEP/WPA/802.1x stuff I will have real end-to-end encryption running between me and my internet gateway (did I mention this magic box is going to be my gateway?). Then I set up IPv4 NAT on the soekris, and an IPv6 firewall as well, so it's now the ultimate gateway box. And, I set up 6to4 on the gateway, and configure my powerbook running OS X with ipv6. I've got a free ethernet port on the soekris to connect up local wired computers, and the wireless ethernet interface for my powerbook. What next? 

Now I pull up <a href="http://xmeeting.sourceforge.net/ohphoneX-docs/ohphoneX.html">ohPhoneX </a>, an implementation of ohphone from the OpenH323 group which just happens to support IPv6. Since my powerbook is running over 6to4 it's not behind a NAT in IPv6, so I can send my overseas relatives and friends my powerbook's IPv6 address and they can directly connect to me. No more NAT nastiness, messing around with the DMZ, or whatever, it's a direct connection straight into my powerbook's globally addressable 6to4 address. Now I'm doing internet telephony, for free, over a wireless interface, and it's all totally autoconfigure. 

It would be very sweet if lots of people got up and running with a gateway like this :-) Forget about <a href="http://www.pulver.com/fwd/">Free World Dialup </a>, forget about <a href="http://www.vonage.com/">Vonage </a>, forget about any kind of silly voice gateway. This is the end-to-end internet, not the InterNAT (or NAPT). I pay for my internet service provider to push the bits, and everything else is free. Even though most of the internet isn't running IPv6 yet, we can all use this setup (or a similar one) to build out the next-generation internet :-)
