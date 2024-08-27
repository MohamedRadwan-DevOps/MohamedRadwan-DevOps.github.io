---
layout: post
title:  "Best Configuration of ReSharper for me"
date:   2010-12-20 07:40:05 +0100
---

This configuration is what I need to do with ReSharper after a clean installation, it may fit with anyone else like me who has the same considerations with ReSharper. 

> I will add and modify this post as my current needs so expect adding or removing configuration as needed in the future.
{: .prompt-info }

- Cache

Make the cache outside the project folder for better with source control so you don't need to make source control ignore this folder especially sometimes when we compare files local vs. server (TFS) it will compare
these files (cache) and you don't need them so you can have a good and clear comparison But remember it is better that if you delete your solution or project to delete the corresponding cache since it will not
deleted because it's not inside the project folder anymore

![ResharperCache](/assets/img/2010/12/ResharperCash.jpg)

- Shortcut and integration with Visual Studio

I chose ReSharper 2.x / IDEA scheme inspired by the community it may fit more with Java but I choose it and became familiar with it

![ResharperShortCutScheme](/assets/img/2010/12/ResharperShortCutScheme.png)

you can download it from here [http://www.jetbrains.com/resharper/documentation/documentation.html](http://www.jetbrains.com/resharper/documentation/documentation.html "Shortcuts download")

-   Auto insert parentheses and quotes
-   Highlight the current line

Actually I didn\'t prefer this I used to use it and when the auto insert parentheses come you can\'t see the method signature and this is not good for me

![ResharperAutoInsertPairParentheses](/assets/img/2010/12/ResharperAutoInsertPairParentheses.jpg)

![VisualStudioCurrentLineColor](/assets/img/2010/12/VisualStudioCurrentLineColor.png)

- IntelliSense

I prefer Visual studio IntelliSense

![ResharperIntelliSence](/assets/img/2010/12/ResharperIntelliSence.png)

- Complete code behaviour

![ResharperAutomaticallyInsertParentheses](/assets/img/2010/12/ResharperAutomaticallyInsertParentheses.jpg)

- Line wrapping

![ResharperLineWrapping](/assets/img/2010/12/ResharperLineWrapping.png)

- Add using Namespaces

![ResharperNameSpaceImports](/assets/img/2010/12/ResharperNameSpaceImports.png)
