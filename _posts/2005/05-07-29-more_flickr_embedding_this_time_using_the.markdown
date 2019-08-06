---
layout: post
title: More flickr embedding, this time using the flickr badge 
---


So actually the <a href="http://www.flickr.com/badge_new.gne">flickr badge </a>code is pretty flexible. More than I realized before. I think It's better than the <a href="/weblog/2005/07/22">flash thing I tried before </a>. Here I will embed 10 random pictures from my trip to barcelona.<div><style type="text/css">div.flickr_badge_image { display: inline; margin: 0.4em; } </style><script type="text/javascript" src="http://www.flickr.com/badge_code_v2.gne?count=10&amp;display=random&amp;size=s&amp;layout=x&amp;source=user_set&amp;user=20938094%40N00&amp;set=261728"/></div>

You can click on them and go to the flickr page for the photo. 

And here's the code.<textarea rows="5" cols="50"><div><style type="text/css">div.flickr_badge_image { display: inline; margin: 0.4em; } </style><script type="text/javascript" src="http://www.flickr.com/badge_code_v2.gne?count=10&amp;display=random&amp;size=s&amp;layout=x&amp;source=user_set&amp;user=20938094%40N00&amp;set=261728"/></div></textarea>

And here's some more information about those options. You embed the options as URL query parameters.<ul><li>count=8 // or any other number </li><li>size={s,t,m} // square, thumbnail, mid-size </li><li>layout={v,h,x} // vertical, horizontal, none </li><li>user={#} // e.g. 20938094%40N00 for me </li><li>source={user_tag, user_set} // maybe other options </li></ul>

If you set source to <code>user_tag </code>then you need to specify<ul><li>tag=barcelona // or some other tag </li></ul>

If you set source to <code>user_set </code>then you need to give<ul><li>set={#} // e.g. 261728 for my barcelona set </li></ul>

For the CSS portion, they give you all kinds of extraneous CSS when you use the <a href="http://www.flickr.com/badge_new.gne">badge generator </a>that you don't need. Just set whatever you want for <code>div.flickr_badge_image </code>at a minimum. 

In order to discover the exact formatting and CSS classes and everything, you can open the URL for the script in your browser, and then look at the source. <a href="http://www.flickr.com/badge_code_v2.gne?count=10&amp;display=random&amp;size=s&amp;layout=x&amp;source=user_set&amp;user=20938094%40N00&amp;set=261728">here's mine for this particular example </a>.
