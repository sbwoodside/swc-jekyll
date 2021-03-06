---
layout: post
title: XSLT code to create XML output from XML in an &lt;xsl:variable&gt; 
---


Here's some code I just wrote in order to parse out XML from a string in XSLT. In XSLT, URL parameters are received in the string type. You can't just copy them into the output because they will be fully entity encoded. So, let's say you wanted to have a form field where someone could enter XHTML, and then you'd store that into an XML file. Of course you don't want to store &lt;p&gt;whatever...&lt;/p&gt; into the file. So you have to actually process the incoming string and then create output XML elements as you go. In order to get you started here's some XSLT code that does an OK job of this:

It's pretty easy to call into, just do something like this:

<pre>&lt;xsl:call-template name="parseXMLParam"&gt;
&#160;&lt;xsl:with-param name="input" select="$url_content"/&gt; 
&lt;/xsl:call-template&gt;
</pre>

... and that's about it. I think it should generally work for XHTML, but I think that it may fail if there are nested elements with the same name (e.g. a para inside a para) or nested loops of names. However as I said since that doesn't happen much in XHTML it should be useful for that at least.
