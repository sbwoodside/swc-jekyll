---
layout: post
title: Virtual PC 6 sucks
---


I just got off the phone with "Daniel M."* from Microsoft technical support. I called them because I was having trouble setting up a network connection between VPC and the host Mac OS X machine. Specifically, Windows 2000 and Panther. But I also had the same problem with a Linux (debian) system I also set up on Virtual PC. 

I figure Daniel is second-tier support because he called me and he doesn't have any way for me to call him back. I asked because my cell phone has a new area code and a lot of PBX systems are unable to dial it. I wanted to call him back from the cell phone so I could use the speaker-phone support it has but -- no, this was not possible. 

What Daniel told me is that networking is not supported by Virtual PC. "Virtual PC", he said (this conversation took place just a few minutes ago) "was only originally designed to connect to the web, the internet. Virtual Switch, for local networking, was just something added by Connectix but when Microsoft bought it, it's not really supported any more. We just left it in as a convenience. But it's not within our support boundaries. There's too many different possible network configurations." 

I said, "so are you telling me that Virtual PC does not support local-area network connections?" His answer, "Yes." 

Daniel is not the first tech support person I talked to. First I spoke with Michael, yesterday. Michael gave me my case number, SRX 0403 22605 XXX. For about an hour I tried to explain my problem to Michael. What I wanted to do, I said, was to do networking between the "guest" and the "host" computer. The "host" is my powerbook running OS X. The "guest" is Windows 2000 running inside Virtual PC. It seems (to me...) that it's a no-brainer that you should be able to connect between the two. But you can't. Even with Virtual Switch, you get two different IP addresses, and VPC fakes out the system with a fake ethernet address, and other computers (such as the iMac) see them as two separate machines. But you can't connect between them on my powerbook. 

In fact currently in order to ssh between OS X and VPC I have to ssh first to my iMac, then back to VPC. 

Not that anyone at Microsoft technical support has ever heard of ssh. They've heard of telnet though, and it just happens that Windows 2000 comes with a built-in telnet server. I could prove to Michael that it wasn't working because I could telnet from iMac to Windows 2000, but I COULD NOT telnet from powerbook OS X to powerbook Windows 2000. 

Eventually, after about an hour, Michael tried to punt me to the Windows networking team. Now, I already know this is not a windows problem. Why? Because I tried the same thing in Linux and had the same problem. I knew he was trying to get rid of me and Windows people would not be able to help so I asked to speak to his supervisor. He connected me quickly. Finally, I thought, I was getting somewhere. 

The supervisor's name is Kal "manager for support". Kal had the mistaken impression from Michael's write- up, that all I wanted to do was telnet. No, I patiently explained, I want to be able to do full networking back and forth between guest and host – file sharing, telnet, even browsing web servers I would set up on the opposite virtual system. Kal said he'd look into it and call me back. 

That takes me to today with the call back from Daniel. Daniel was pessimistic from the start. He'd never heard of ssh either, and he wanted to try something "simpler" – windows networking. At this point I realized I wasn't going to get anywhere. He then proceeded to disclaim for a while that it wasn't really supported anyway. 

So, Virtual PC doesn't support networking. Who knew? I should ask for my money back. 

* last name removed to protect the maybe innocent. 

<strong>Update </strong>2004/03/23: Virtual PC Help says: "Under Mac OS X, a PC may communicate with the host Macintosh, with other PCs using the Virtual Switch, and with other computers on the network." 

<strong>Update </strong>2004/03/24: I talked to Daniel again today. He said he'd brought it up in a meeting and so I think he meant to say he was taking it seriously. I told him about reports I'd read on their own newsgroups that wireless networking was responsible for the problem. Later, I found <a href="http://simonwoodside.com/weblog/2004/03/24">a solution </a>.
