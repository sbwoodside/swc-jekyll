---
layout: post
title: Better reading with google 
---

So let's say you are reading along and you want to read MIT's Technology Review article: [A Remote Control For Your Life](http://www.technologyreview.com/articles/mann0704.asp) . And then they want you to pay and you don't want to pay. OK, fine but how is it that the content of the article got indexed into google in the first place? Well as it turns out, they just check the User-Agent string on the HTTP requests. So if you were clever you would just do this:

```
curl -O -A 'Googlebot/2.1 (+http://www.googlebot.com/bot.html)'  'http://www.technologyreview.com/articles/mann0704.asp?p=0'
```

and then you can read the article. There are other sites that play similar tricks.
