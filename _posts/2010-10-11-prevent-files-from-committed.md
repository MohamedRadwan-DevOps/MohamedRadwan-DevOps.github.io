---
layout: post
title:  "How to prevent some files from committed to the source control?"
date:   2010-10-22 07:40:05 +0100
---

I will show another small tip which prevent file from committed to the source control or TFS 2010, I will  prevent the generated minifiy file that create by Microsoft Ajax Minifier. 

[![Open Check-in policy](/assets/images/2010/10/ProjectSettings.png)](/assets/images/2010/10/ProjectSettings.png)

- Open forbidding pattern policy

[![Forbidden policy](/assets/images/2010/10/AddCheck-inPolicy.png)](/assets/images/2010/10/AddCheck-inPolicy.png)

- Enter reguler expression that prevent .minifie files from from committed 
  
  [![Regular Expression](/assets/images/2010/10/PatternforMini.jpg)](/assets/images/2010/10/PatternforMini.jpg)

Done.