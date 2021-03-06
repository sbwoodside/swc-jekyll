---
layout: post
title: mailman RSS, and virtual hosts on localhost 
---


In 2003, on the W3C www-rdf-interest mailing list, <a href="http://lists.w3.org/Archives/Public/www-rdf-interest/2003Feb/0047.html">Dan Brickley wrote </a>:<blockquote>I just stumbled across this after an #rdfig discussion about adding RSS support to Mailman, the popular list management and HTML archiving package. Turns out the patch exists already (but wasn't intergrated yet). It took me less than 10 minutes to patch my Mailman installation and rebuild the archives for rdfweb-dev. I now have http://rdfweb.org/pipermail/rdfweb-dev/rss.xml generated automatically. See http://rdfig.xmlhack.com/2003/02/09/2003-02-09.html#1044813421.381747 for the (trivial to apply) patch and related info. Just cd into the Mailman/Archiver/ directory and do 'patch &lt; ~danbri/rss.patch' or whatever, then re-run bin/arch on your archives. The markup exported is fairly basic, but sets things up nicely for future extensions -- you could add in richer descriptions of the mailing lists fairly easily, though I'm not sure how best one would hook such information up to Mailman's www-based frontend. </blockquote>

Well, I can attest that it really is (still) that easy. <a href="https://sourceforge.net/tracker/index.php?func=detail&amp;aid=657951&amp;group_id=103&amp;atid=300103">Get the latest patch from the bug tracker </a>- right now it's <a href="https://sourceforge.net/tracker/download.php?group_id=103&amp;atid=300103&amp;file_id=55489&amp;aid=657951">here </a>. OK, the patch isn't perfect - you have to remove the mail headers at the top, and the file <code>Defaults.py.in </code>should be actually applied to <code>Defaults.py </code>. But aside from that it works really, really well. 

The other thing I wanted to note is this article on ONLamp.com: <a href="http://www.onlamp.com/pub/a/apache/2003/07/24/vhosts.html">Simplify Your Life with Apache Virtual Hosts </a>because it explains how to set up virtual hosts on your home/development box. The trick is to edit <code>/etc/hosts </code>I guess.
