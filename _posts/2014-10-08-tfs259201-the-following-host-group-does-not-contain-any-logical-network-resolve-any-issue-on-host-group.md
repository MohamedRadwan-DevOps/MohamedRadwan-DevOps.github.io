---
layout: post
title: "TFS259201 the following host group does not contain any logical network Resolve any issue on host group"
date: 2014-10-08 16:13:43 +0100
---

In [Team Foundation Server](http://msdn.microsoft.com/en-us/vstudio/ff637362.aspx "Visual Studio Team Foundation Server 2013"), if you try to create [SCVMM Lab Environment](http://msdn.microsoft.com/en-us/library/ee943322.aspx "SCVMM (virtual) environments") and you encounter the following error: 

TFS259201 the following host group does not contain any logical network Resolve any issue on host group
{: .prompt-danger }

![TFS259201](/assets/img/2014/10/tfs259201.png)

You can solve this issue as the following: 

Add logical network as the following: 

![SCVMM Logical Network](/assets/img/2014/10/scvmm-logical-network.png)

As we can see the created logical network was not associated with network adapter

![Logical Network assign network adapter](/assets/img/2014/10/logical-network-assign-network-adapter.png)

Add a network adapter to the logical network 

![Assing Logical network](/assets/img/2014/10/assing-logical-network.png)
