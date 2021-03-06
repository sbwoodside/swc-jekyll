---
layout: post
title: sudo apachectl stop && sudo apt-get remove apache2 && sudo apt-get install nginx
image: nginx-logo.png
---


I binned apache finally on semacode.com. It was easy. A little bit of "this is really the last straw" frustration with mod_rewrite and I ditched it.

I've been threatening to leave you, apache, for years. Ever since I first cursed your horrid rewriterules, I knew that it would never be the same between us. You were good, once. You weren't just "a patchy" web server, but a scrappy one... once. But 2.0 you just didn't live up. You didn't fix your big warts. You got flabby. Even the decision by your developer team to <a href="https://issues.apache.org/bugzilla/show_bug.cgi?id=13986">finally remove the default MIME type</a> didn't redeem you in my eyes.

No, it was just one poke in my eye too many, when you insisted on unencoding my percent encoded URLs before passing them to the rails/mongrel proxy, and there was just no way to make you stop doing it, no matter how many googles I searched. And so I said: enough is enough. Everyone on Rails uses <a href="http://wiki.nginx.org/">nginx</a> now, and I will too. I'm tired of learning how to sacrifice chickens to the apache configuration gods. Bring me something new, clean, shiny, fast, and easy to configure!

Learning how to configure nginx took an hour on the outside -- it's very easy and keeps all the good parts of apache's syntax and throws away the complete crap. It even allows me to compress stupid blocks into one-liners! :

<pre>  if (-f $document_root/system/maintenance.html) { rewrite  ^(.*)$  /system/maintenance.html last; break; }</pre>

Isn't that gorgeous! I agree. And so the "engine x" russians get my love now. It's all over. Sayanora. End communication.
