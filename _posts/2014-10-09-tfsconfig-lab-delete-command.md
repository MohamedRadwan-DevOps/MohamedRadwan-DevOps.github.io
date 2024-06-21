---
layout: post
title: "TFSConfig Lab /Delete Command"
date: 2014-10-09 11:36:44 +0100
tags: [tfsconfig-lab]
---

In a previous post, I explained when you should and should not remove Lab Management resources like (Templates, VMs, Environments). For more information [click here](https://mohamedradwan-devops.github.io/tag/tfsconfig-lab/ "Do I need to remove Lab Management from a Collection when I Upgrade?").

In this post, I will show and explain the different options for TFSConfig Lab /Delete switch.

## [What will happen if we run the following command:]

```xml
tfsconfig lab /delete /collectionName:DefaultCollection
```

This will remove all lab management resources from the collection but it will leave them in SCVMM, see the following video:

{% include embed/youtube.html id='AGxtxDjU9P8' %}

## [What will happen if we run the following++command with /External switch:]

```xml
tfsconfig lab /delete /collectionName:DefaultCollection /external
```

This will remove all lab management resources from the collection and also remove them from SCVMM and the Hyper-V host, see the following video:


{% include embed/youtube.html id='HiS5VLPjsRo' %}

>For more information about TFSConfig lab /delete command, [click here](http://msdn.microsoft.com/en-us/library/ee712732.aspx)
{: .prompt-info }

