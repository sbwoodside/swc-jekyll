---
layout: post
title: Better reading with google 
---
<p>So let's say you are reading along and you want to read MIT's Technology Review article: <a href="http://www.technologyreview.com/articles/mann0704.asp">A Remote Control For Your Life </a>. And then they want you to pay and you don't want to pay. OK, fine but how is it that the content of the article got indexed into google in the first place? Well as it turns out, they just check the User-Agent string on the HTTP requests. So if you were clever you would just do this: </p><pre>curl -O -A 'Googlebot/2.1 (+http://www.googlebot.com/bot.html)'  'http://www.technologyreview.com/articles/mann0704.asp?p=0' </pre><p>and then you can read the article. There are other sites that play similar tricks. </p>
