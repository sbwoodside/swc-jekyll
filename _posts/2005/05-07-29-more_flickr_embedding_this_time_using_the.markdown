---
layout: post
title: More flickr embedding, this time using the flickr badge 
---


So actually the [flickr badge](http://www.flickr.com/badge_new.gne) code is pretty flexible. More than I realized before. I think It's better than the [flash thing I tried before](/weblog/2005/07/22) . Here I will embed 10 random pictures from my trip to barcelona.

```
<style type="text/css">div.flickr_badge_image { display: inline; margin: 0.4em; } </style>
<script type="text/javascript" src="http://www.flickr.com/badge_code_v2.gne?count=10&amp;display=random&amp;size=s&amp;layout=x&amp;source=user_set&amp;user=20938094%40N00&amp;set=261728" />
```

You can click on them and go to the flickr page for the photo.

And here's the code.

```
<div><style type="text/css">div.flickr_badge_image { display: inline; margin: 0.4em; } </style><script type="text/javascript" src="http://www.flickr.com/badge_code_v2.gne?count=10&amp;display=random&amp;size=s&amp;layout=x&amp;source=user_set&amp;user=20938094%40N00&amp;set=261728"/></div>
```

And here's some more information about those options. You embed the options as URL query parameters.

*   count=8 // or any other number
*   size={s,t,m} // square, thumbnail, mid-size
*   layout={v,h,x} // vertical, horizontal, none
*   user={#} // e.g. 20938094%40N00 for me
*   source={user\_tag, user\_set} // maybe other options

If you set source to `user_tag` then you need to specify

*   tag=barcelona // or some other tag

If you set source to `user_set` then you need to give

*   set={#} // e.g. 261728 for my barcelona set

For the CSS portion, they give you all kinds of extraneous CSS when you use the [badge generator](http://www.flickr.com/badge_new.gne) that you don't need. Just set whatever you want for `div.flickr_badge_image` at a minimum. In order to discover the exact formatting and CSS classes and everything, you can open the URL for the script in your browser, and then look at the source. [here's mine for this particular example](http://www.flickr.com/badge_code_v2.gne?count=10&display=random&size=s&layout=x&source=user_set&user=20938094%40N00&set=261728) .