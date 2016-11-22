---
layout: post
title: Alexandra thoughts 
---
<p>After the first release of Alexandra, I discussed with several people a major flaw, which was that it did not preserve the RNG order as given in the schema when it added or changed elements. I was concerned I would need to use some sort of database update-type scheme. I wasn't keen on this as the only xml update project that seemed to be anywhere near a state of completion was XUpdate and it wasn't very complete, and also seemed like a hassle. I realized later that I could generate XSLT to do the update. More recently I was working on how to pass through the positioning information for both elements that are already instantiated and ones that aren't. I seem to have that completed now. So, at this point I believe it is possible to generate only RNG-valid instances using alexandra. </p>
