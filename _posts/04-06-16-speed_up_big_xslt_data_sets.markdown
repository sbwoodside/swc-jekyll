---
layout: post
title: speed up big xslt data sets 
---


A recent thread on axkit-users brought me this tip. If you have an XML data store with a large number of nodes, you can use xsl:key to pre-create an index on the table. David Nolan (of CMU) wrote (link not available, sorry)<blockquote>

Basically xsl:key (I mis-remembered the prefix before...) pre-creates an index on the table, based on whatever attributes/nodes you choose. For example, if your xml looks like:<pre>&lt;foo&gt; &lt;bar name="X"&gt;...&lt;/bar&gt; &lt;bar name="Y"&gt;...&lt;/bar&gt; ... &lt;/foo&gt; </pre>

And you need to select "/foo/bar[@name='X']", doing so directly is cheap if your XML is small. But if its big you should create a key, especially if you're doing selections of that type often. So before your templates you do:<pre>&lt;xsl:key name="bar_by_name" match="/foo/bar" use="@name"/&gt; </pre>

Then when you need a piece of data you use "key('bar_by_name','X')". 

You can even make up a concatenated index, if you need a multi-part search. i.e.:and then select "key('foo',concat($foo_name,'-',$foo_type))". Just make sure the string you're using to separate the search elements isn't valid as part of the content of the elements. 

Proper application of xsl:key can be very useful. One of our (non-AxKit) translations is taking flat database dumps with approximately 10,000 nodes and converting them to a structured format, based on the structure of our database, with approximately 145,000 nodes. Using xsltproc (which is slower than Saxon, but more widely available) that translation takes 30-40 seconds. Without keys it was taking over 10 minutes.</blockquote>
