---
layout: post
title: "Using Network Isolation in Lab Management and Solving Some Issues"
date:   2012-03-04 11:55:39 +0100
---

In this post, I will describe how we can use the network isolation capability of [Lab Management](https://mohamedradwan-devops.github.io/category/alm/test-lab-center-2010/ "Lab Management ") in [MTM (Microsoft Test Manager)](https://mohamedradwan-devops.github.io/category/alm/mtm-11/ "MTM 11 Beta"). I will also show how to solve some issues I faced. This video is part of my whole [guide](https://mohamedradwan-devops.github.io/poststfs-2010-enterprise-video-guide/ "TFS Enterprise Installation and Configuration Guide") of "[TFS 2010 Enterprise Installation and Configuration Guide](http://tfs10enterprise.codeplex.com/ "TFS Enterprise Guide")" that is published on [CodePlex](http://tfs10enterprise.codeplex.com/ "TFS Enterprise Guide"). For more information about the whole installation and configuration, see the guide on [CodePlex](http://tfs10enterprise.codeplex.com/ "TFS Enterprise Guide").

{% include embed/youtube.html id='uYFZFAYgodU' %}

### Issue 1: TF260073 Incompatible Architecture Error

The first issue I faced was [TF260073 incompatible architecture error when trying to deploy an environment in Lab Manager]. This error can happen for many reasons. It happened to me because the LabAD (Active Directory) machine was not able to deploy to the host (Hyper-V) machine that I assigned for the TFS Lab Management. This was because LabAD (Active Directory) was created on the server at my work and the processor was not supported in my home environment. When I tried to change the property of the machine to support different process architecture while it was stored in the library, it couldn't save the changes. So, I just copied the VHD file from the library to the desired host and then created a VM based on that VHD. I then stored the created VM in the library again from this host that would deploy it later. My advice, if this problem happens, is to use SCVMM to deploy the machine on the desired host and solve the problem first, and then return to Lab Management.

### Issue 2: TF267055: Unable to Connect to the Controller

The second issue I faced was [TF267055: The machine is not ready to run tests because of the following error: Unable to connect to the controller on '<TestControllerFQDN>:6901'. Reason: No such host is known. Make sure the test controller is online and the firewall on the test controller is not blocking the connection]. This happened because the Test Agent can't resolve the Test Controller machine name. I tried many solutions, like adding the Test Controller machine IP with name in the host file, but no matter what, the IP resolved differently. We know that any machine working in an isolated network will have two virtual network adapters, one for private network and one for external network, and each has its own DNS. So, the solution was to add the Test Controller record in the private Domain LabAD (Active Directory) in my case, and everything worked great.

For any help, just contact me :-) For more information about Network Isolation on MSDN, you can visit the following link: [http://msdn.microsoft.com/en-us/library/ee830480.aspx#NetworkIsolatedEnvironments](http://msdn.microsoft.com/en-us/library/ee830480.aspx#NetworkIsolatedEnvironments "MSDN")
