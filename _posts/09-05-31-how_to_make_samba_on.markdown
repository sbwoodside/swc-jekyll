---
layout: post
title: How to make samba on ubuntu use your unix passwords
---


You need something called "password sync" ... obvious right?

This will help:

<a href="http://jaka.kubje.org/2007/05/14/unix-samba-password-sync-on-debian-etch/">Unix and Samba password sync on Debian Etch</a>

...only took me an hour to figure out how to get logging working and decode the obscure error messages....

This is probably what you want to do if you get this:

<pre>Authentication for user FAILED with error NT_STATUS_WRONG_PASSWORD</pre>
