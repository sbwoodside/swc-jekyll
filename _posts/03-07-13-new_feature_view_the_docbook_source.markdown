---
layout: post
title: New feature, view the docbook source 
---
<p>So, I added a feature to view the docbook source for those documents that actually have it. So far it's only activated in the ICT section but I'll probably turn it on for the other parts as well. The idea is just that you can add ?show_source=YES to the end of the URL and get the DocBook (XML) source. If it's not DocBook, nothing will happen because everything else is just XHTML anyway, you might as well just view the source in the browser. </p><p>AxKit already has a way to do this using configuration directives in the apache configuration files (aka .htaccess) but I've been avoiding config directives up to now and using Processor Includes (PIs) instead. It fits with my document-centric view of how this should all work. It wasn't too hard to reproduce the function in XSLT, using a &lt;param&gt; and I just had to add a bit of code to Norman's XSLT for DocBook and little code in another place. </p>
