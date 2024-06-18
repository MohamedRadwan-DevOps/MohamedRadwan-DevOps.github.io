---
layout: post
title: "Copy comments from base in Resharper"
date:   2011-10-31 04:09:33 +0100
---

I used to use a very slickly feature of Resharper which is copy comments
from base (class or interface), anyone knows me will know that I am very
strict to code guidance and rules using style copy and other
code standard tools, we have very restricted rules about documentation,
so this really helped me very well but\....?! 

The problem that the action context of this action sometimes didn\'t appear, until
this moment I didn\'t know why? of course I Google everywhere but
nothing helpful except that info that Resharper 6.0 doesn\'t support the
style cop plugin till now, which was very sad news for me anyway, here
what I do to fix the problem, of course it fixed at the end but I
didn\'t know why??

-   I disable the Style copy for Resharper plugin
-   I remove the old comments
-   I remove the inheritance and bring it again

And now its working with style copy an without style cop, Just click on
the method name and the context action will appear and include the copy
comments from base
[![CopyCommentsFromImplementation](/assets/images/2011/10/CopyCommentsFromImplementation.png)](/assets/images/2011/10/CopyCommentsFromImplementation.png)

[![CopyCommentsFromImplementation2](/assets/images/2011/10/CopyCommentsFromImplementation2.png)](/assets/images/2011/10/CopyCommentsFromImplementation2.png)

