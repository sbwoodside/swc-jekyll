---
layout: post
title: Configuring awstats for Debian Sarge 
---


It seems that AWStats is without a doubt the best stats package out there these days. And you can get it easily enough on debian with apt-get. But it still requires a bit of configuration. Here's what I've done so far. 

First I have a number of virtual hosts so that I made a copy of <code>/etc/awstats/awstats.conf </code>to <code>/etc/awstats/awstats.semacode.org.conf </code>which is the blessed name for each virtual host. In that new conf file you need to have:<ul><li><code>LogFile="/var/log/apache/access.log" </code></li><li><code>LogFormat = 1 </code>- this is important because Sarge comes with apache configured to the <code>combined </code>setting at least in my recently-made fresh install. </li><li><code>SiteDomain="semacode.org" </code></li></ul>

Now, apt-get will already have installed a cron job for you, but you need to make sure it's working because it won't complain if it's broke. So do this: <code>sudo /usr/lib/cgi-bin/awstats.pl -config=semacode.org </code>and it will complain if there's anything wrong. 

Finally you will need to add the following line to your httpd.conf file: <code>Alias /awstats-icon "/usr/share/awstats/icon/" </code>. 

I also am going to add password protection to my awstats page so that the general public can't access it. Partly because it could be a security concern, but mainly because it's slooooow.
