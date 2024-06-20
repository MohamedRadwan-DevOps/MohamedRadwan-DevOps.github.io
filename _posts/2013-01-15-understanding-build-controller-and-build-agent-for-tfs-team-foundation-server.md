---
layout: post
title: "Understanding Build Controller and Build Agent for TFS (Team Foundation Server)"
date: 2013-01-15 23:45:27 +0100
---

In this post, I will explain the **Build Controller** and the **Build Agent** in Team Foundation Server (TFS). Below is a step-by-step video for the post:

{% include embed/youtube.html id='K9s11aLPPgI' %}


The Build Service is a Windows Service that can only have one **Build Controller**, which is configured for only one **Team Project Collection** and can have multiple **Build Agents** as needed. While it is possible to have multiple **Build Controllers** on the same machine, it is not recommended in a production environment. For more information, see [Configuring Multiple TFS Build Controllers on the Same Machine](https://mohamedradwan-devops.github.ioposts/configuring-multiple-tfs-build-controller-on-the-same-machine/ "Configuring Multiple TFS Build Controller on the Same Machine"):

![1-Build-Service-resources-3](/assets/images/2013/01/1-build-service-resources-3-1.jpg?w=660)

Only one **Build Controller** can exist on the same machine. We can have a **Build Controller** running with the TFS AT (Team Foundation Server Application Tier), but it is not recommended to have the **Build Agent** on the TFS AT because the **Build Agent** performs intensive work, which can slow down the TFS AT.

![2-Build-Controllers-and-Build-Agents-3](/assets/images/2013/01/2-build-controllers-and-build-agents-3-1.jpg?w=660)

>For more information about how to work with **Git** with animation, where all commands are represented in graphical animation (e.g., git branch, git merge, git rebase, git cherry-pick, and many others), see [Mastering Git with animation](https://mohamedradwan-devops.github.ioposts/mastering-git-from-beginner-to-advanced-step-by-step-with-graphical-animation-commands/)

Here is an example of a Build Server that has one **Build Controller** configured for one **Project Collection** and multiple **Build Agents**:

![3-Build-Service-example-3](/assets/images/2013/01/3-build-service-example-3-1.jpg?w=660)
![4-Build-Service-one-controller-multi-agents](/assets/images/2013/01/4-build-service-one-controller-multi-agents.png?w=660)

Removing the build configuration allows us to reconfigure and see the number of recommended **Build Agents** and the **Windows Service**:

![5-Remove-Build-configuation](/assets/images/2013/01/5-remove-build-configuation-1.png?w=660)

If the Build is not configured, we can see that there is no Windows Service:

![6-Build-Service-not-exist-before-configure-build-service-on-tfs](/assets/images/2013/01/6-build-service-not-exist-before-configure-build-service-on-tfs-1.png?w=660)

The Windows Service for the build exists if the build is configured (Registered):

![7-Build-Service-exist-after-configure-build-on-tfs](/assets/images/2013/01/7-build-service-exist-after-configure-build-on-tfs-1.png?w=660)

When the processor count is one, the available **Build Agent** count is two, and the recommended count is one:

![8-Number-of-build-agents-is-depend-on-number-of-processors-2](/assets/images/2013/01/8-number-of-build-agents-is-depend-on-number-of-processors-2-1.png?w=546)

>For more information about how to work with Kubernetes clusters and deploy them to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see [Kubernetes cluster for beginner](https://mohamedradwan-devops.github.ioposts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/%20)

When the processor count is four, the available **Build Agent** count is eight, and the recommended count is one:

![9-Number-of-build-agents-is-depend-on-number-of-processors-1](/assets/images/2013/01/9-number-of-build-agents-is-depend-on-number-of-processors-1-1.png?w=539)

>For more information about how to work with **Docker**, including pulling Docker images, running Docker images, and working with containers, see [Docker for beginners](https://mohamedradwan-devops.github.ioposts/docker-for-beginners-step-by-step-tutorial/)

Links:
[Scale out Your Build System](http://msdn.microsoft.com/library/dd793166.aspx "Scale out Your Build System ")
