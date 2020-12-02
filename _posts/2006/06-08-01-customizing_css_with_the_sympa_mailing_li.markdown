---
layout: post
title: Customizing CSS with the Sympa Mailing List manager .. and CFH 416
---


I recently decided to customize the CSS style sheets on my <a href="http://www.sympa.org/">Sympa mailing list manager </a>-based <a href="http://lists.semacode.org">semacode.org forums </a>. It wasn't quite as easy as I think it should have been. The "instructions" in the Sympa docs are not exactly friendly. However after puzzling through it myself I found that it wasn't too hard. Here are the notes I made in the process.

<pre>set css_path in robot.conf e.g. css_path /var/www/lists.semacode.org/css #filesystem path css_url http://lists.semacode.org/css/ #fully-qualified URL! then set chmod the css directory, chmod a+rw so that sympa can change it then on "skins admin" page do "install static css" (static = not generated on the fly by tt2, I think) it will install style.css and some other .css files in the css directory then set the css directory back to whatever permissions you want it to have then modify the "static" css files however you like </pre>

...and there you have it. So far I haven't done much, just a little bit on the <a href="http://lists.semacode.org/sympa/arc/appdev">archives view </a>. Ultimately I hope to steal all the good looks from projects like <a href="http://www.phpbb.com/">phpbb </a>and others. 

Also my next appearance on <a href="http://callforhelptv.com/">Call for Help </a>should be in episode #416, whenever that airs.
