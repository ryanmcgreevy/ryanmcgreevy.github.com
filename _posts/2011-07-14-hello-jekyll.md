---
layout: post
title: Hello Jekyll!
---

Hello Jekyll!  After a long downtime in maintaining my website, I decided to redo it completely with 
<a href="https://github.com/mojombo/jekyll/wiki">Jekyll</a>.  Jekyll is a blog aware, static site generator developed by the same guy
behind <a href="https://github.com/">GitHub</a>.  As a programmer, I liked the idea of my website existing as portable, flat files
that can be published (and maintained) using a version control system (git).  I previously used WordPress for my site, which while convenient,
never quite gave me the feeling that I knew where everything was and how it truly worked.  Now with Jekyll, I can develop my site in the same 
manner as my code, resting assured that I have all of my content safely (and easily) versioned and backed up locally and on GitHub.  

Because Jekyll generates a static html site, I can also put the entire site on <a href="http://aws.amazon.com/">Amazon's S3</a>, part 
of their web services suite.  S3 is a storage solution that can also host static html website with the click of a button.  
This allows me to mirror the entire site on S3 in case of a problem with GitHub and quickly redirect traffic as needed. S3 will also be used
to host any large files for the site, as GitHub site hosting is a free privelege that shouldn't be abused.  Ultimately I
hope that this change to Jekyll will get me to see my website as just another project to tinker with and keep me interested.  Hopefully
my site will no longer be some remote foreign application that I *should* update, but instead something I *want* to update.
