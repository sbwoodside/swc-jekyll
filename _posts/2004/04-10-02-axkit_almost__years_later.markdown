---
layout: post
title: axkit almost 2 years later
---


It's getting close to the 2 year anniversary of when I <a href="/weblog/2002/12/28">first started </a>using <a href="http://axkit.org">AxKit </a>. Ever since Matt Sargent posted his <a href="http://maclux-rz.uibk.ac.at/maillists/axkit-users/msg07213.shtml">success story </a>on axkit-users I've been thinking about my own success story with AxKit, it's been highly satisfying. 

Matt <a href="http://maclux-rz.uibk.ac.at/maillists/axkit-users/msg07219.shtml">followed up </a>by saying:<blockquote>Currently around 10 backend servers (two separate sites) doing about 5 million "hits" a day (almost all of that is the spam incoming from our mail servers, and is handled by a lightweight mod_perl handler, not AxKit). I say "about" because we don't monitor the traffic very carefully - we do problem based reporting - we're not interested in maximising our hits :-) </blockquote>

In my experience with my site having been slashdotted and boingboing'ed (I had in one day 120 000 hits and 19 000 pages without breaking a sweat) the performance has been very smooth on a minimal box. This is all due to caching - when I left caching off another time the server got totally slugged (oops) due to a boingboing'ing. 

I never replied to Matt's thread but I want to say that when I picked AxKit it was partially due to the promise of fantastic scalability due to caching - and that's been borne out for me by experience.
