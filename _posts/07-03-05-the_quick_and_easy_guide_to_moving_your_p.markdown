---
layout: post
title: The Quick and Easy Guide to moving your project from CVS to Subversion 
---
<p>So you want to use SVN? Fine, it's easy to move a project from one to the other. </p><p>Get <a href="http://cvs2svn.tigris.org/">cvs2svn </a></p><p>Go to a checked out copy of your cvs project and run <code>cvs admin -kb filename </code>on any binary files. </p><p>Commit to CVS. </p><p>Assuming that you've got a simple CVS project with no branches that you want to keep, do this: </p><pre><code>./cvs2svn-1.5.1/cvs2svn --trunk-only -s project-name /path/to/cvs_repository/project-name mv project-name /path/to/svn_repository/ </code></pre>
