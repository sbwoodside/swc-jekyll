---
layout: post
title: Two-level tags 
---


<a href="/weblog/2005/07/02">I've thought before </a>about putting in a two-level tagging system on my blog. I guess that it comes from that I'm dissatisfied with "tags" per se. They're just not rich enough. With a simple tagging system, it's hard to organize your tags into groups, for example, which to me is a big problem. 

<em>I'm not the only one to do something about this: see also <a href="http://www.lifehacker.com/software/delicious/organize-delicious-bookmarks-in-tag-bundles-176340.php">tag bundles on del.icio.us </a>, and also "meta tags" (which are tags about tags I guess). </em>

I think that the common "solution" is to give mix tags together, so if you're talking about developing software on OS X you'd tag with "development", "software" and "OS X". But that's an implicit, not an explicit relationship. Also, designing a tag browser that lets you see which articles are tagged with all three of those tags is a hassle. Finally, there's no sense of hierarchy. 

On the other hand, going to hard in the other direction (totally formal hierarchies) is also not viable in my opinion because it's too much work. You can get stuck with a specific hierarchy that doesn't always work (like in a library catalogue), or you can get confused by deranged mazes of hierarchical relationships (like <a href="http://en.wikipedia.org/wiki/Wikipedia:Category_schemes">Wikipedia's categories </a>). 

This is a problem in software development too. I remember when working at Apple. NextStep always had a single-level namespace, which meant that each and every library and application class had to have a unique name. This is a really big hassle and so people wound up prefixing their class names with two uppercase letters in order to prevent collisions. So NSThis and NSThat were the names for "NextStep" classes (provided by the system), and your own app would be MAThis and MAThat (for "My App" ...). Then of course what if two people choose the same prefix. Or what if the name of the app changes, and your prefix becomes historical and a little spurious. (Like in OS X, all of the system classes still start with NS...) 

Apple introduced a two-level namespace at some point in 2001 I think, which made the problem go away (although the NS prefix remains). I think that two-level systems are good. People can remember two levels of hierarchy very easily, it's a sort of natural relationship (like having a filesystem with files and folders but no sub-folders ... wouldn't that be simple??). 

So I decided to put into place a two-level tagging system here in my blog. The "top level" tag is the <strong>category </strong>and the "second level" tag is the <strong>tag </strong>. Top level categories include <a href="/weblog/tag/links">links </a>, <a href="/weblog/tag/original">original </a>, and a big one: <a href="/weblog/tag/dev">dev </a>(for software development). You can see all the categories by clicking "Browse all tags" at the top to take you to the <a href="/weblog/tag/">categories and tags browser </a>. 

There's a couple more things I want to do. One is to integrate the rest of the site into the system, so that any of the pages on the site can be tagged and included in an overall tags-based browser for the site. 

Also I need to improve the UE a bit ... one thing is to have the ability to see a list of each category and its sub-tags. Also, I need a page-overflow paging type system to deal with huge pages like the one for the "dev" tag.
