---
layout: post
title: New server for simonwoodside.com
image: r300.png
---


Yup.

Got a new server.

The old box, was a Penguin Computing rack-mount purchased in 1999 or 2000. It had a PIII and was totally maxed out RAM-wise -- at 512 MB. Anyone who's tried to run rails on a box with that much ram might understand why I had occasional downtime. mongrel would just give up sometimes. Trying to install new gems was fun as well. Still, the old box had a good run.

The new box is a Dell R300... Core 2 Duo... RAM is at 4GB right now, max 24. And we've gone with RAID-1 since we don't really need the space but like the redundancy.

Also, we switched from debian to ubuntu. Ubuntu is a bit less secure but a hell of a lot easier to deal with in terms of package management and installation.
