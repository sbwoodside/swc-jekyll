---
layout: post
title: "DocBook: What's not to like???"
---


Everytime I read about <a href="http://www.docbook.org/tdg/en/html/docbook.html">DocBook </a>there's one thing everyone says, it's complicated. Well I don't get it. DocBook is not complicated. I mean, sure it's got a few hundred different elements, but you don't actually need most of them. You basically need, book, article, section, title, para, ulink, table, and informallist. That's it. All of those, except for section and title, map directly onto XHTML. Section and title, are actually better than HTML once you get used to how they work, and they make the magic that makes DocBook so much better than HTML because it's structured, not just presentational. Then there's the awesome XSLT stylesheets from Norman, so all you really need to do is make a few changes in the params.xsl file and write up a CSS file, and you're set to go. It's got all kinds of nice features like automatic table of contents building, indexing, etc. And if you ever discover you need to add a reference, or a quotation, you just pull out the reference and it explains what to do (with examples). You insert the right tags, and the XSLT does a nice baseline formatting job for you automatically. You can tweak to your heart's content. 

So basically if you start writing with DocBook, you get a lot of good stuff for free. It comes with a bunch of good styling transformations.
