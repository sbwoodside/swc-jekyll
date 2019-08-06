---
layout: post
title: downgrading debian packages 
---


So I kind of managed to screw myself recently by upgrading gcc on my debian stable installation to the testing version to get gcc-3.3. ( <i>First of all, will someone explain to me why gcc 3.3 still isn't in stable yet? That's just bizarre. </i>) So it turns out that the upgrade left me with a non-working symbian toolchain ( <i>something's wrong with wine? it's hard to be certain </i>). 

The OBVIOUS thing to do seems to be to downgrade but wait! apt-get doesn't support downgrades. Instead I'm left with a bizarre situation where somehow I have to rebuild the dependency chain from the top down using older versions of the libs that are in stable. At least now I have learned about the following useful commands.<pre>dpkg --get-selections </pre>

tells you what packages are installed<pre>apt-get install foobar/stable </pre>

installs specifically the stable version of the package foobar. <a href="http://lists.debian.org/debian-testing/2002/09/msg00068.html">Here's a useful thread </a>. 

<b>Update: </b>( <i>BACK UP FIRST! </i>) Hooray! Through a combination of <code>apt-get remove libstdc++5 </code>( <i>which I cancelled </i>) and looking at what it's going to kill, and going through the list looking for the keystone dependencies, I found that the trick was to install the stable version of xlibs, and libstdc++3, and maybe one or two others, but anwyay I think I have it all back to stable now. 

<b>Update #2: </b>I also wound up needing to use <a href="http://biostat.mc.vanderbilt.edu/twiki/bin/view/Main/DependFixDebian">these tricks </a>especially, <code>cd /var/cache/apt/archives/ &amp;&amp; dpkg --force-overwrite --install [package] </code>Note that in the last case, an apt-get clean can make it easier to find the right package.
