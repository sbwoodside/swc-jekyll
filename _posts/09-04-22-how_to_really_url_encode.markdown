---
layout: post
title: How to really URL encode an NSString in Objective-C, iPhone, etc.
---


Trying to encode URL parameters on Mac or iPhone? Frustrated because NSString stringByAddingPercentEscapesUsingEncoding encodes non-URL characters but leaves the reserved characters (like slash / and ampersand &amp;) alone? "Apparently" this is a "bug" apple is aware of, but they haven't done anything about it yet, and so, here is a solution that actually works.

Try this:

<pre>&#160; NSString * encodedString = (NSString *)CFURLCreateStringByAddingPercentEscapes(<br />   &nbsp;NULL,<br />   &nbsp;(CFStringRef)unencodedString,<br />   &nbsp;NULL,<br />   &nbsp;(CFStringRef)@"!*'();:@&amp;=+$,/?%#[]",<br />   &nbsp;kCFStringEncodingUTF8 );</pre>

As an example, @"'Decoded data!'/foo.bar:baz" will become "%27Decoded%20data%21%27%2Ffoo.bar%3Abaz".

Obviously you would use this, not on the full URL, but just on the parameters.
