---
layout: post
title: "Deeply Understanding of Azure Pipelines Agent | Learn How to Install and Configure Azure Pipelines"
date: 2019-10-03 20:33:37 +0100
---

All the content of this post with more details is explained in the following video: 

{% include embed/youtube.html id='IJ1IfKyvxHM' %}


## Intro 

In this post and video, you will deeply learn and understand in detail [Azure Pipelines agent](https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/agents?view=azure-devops). During many conversations and discussions, I have seen a lot of confusion and misunderstanding of Azure Pipelines. In this post and video, I will try to cover and clear all assumptions and provide a deeper understanding of Azure Pipelines agents.

First, we will see the difference between the Azure Pipelines hosted agent and the self-hosted agent or the private agent. We will understand deeply what the difference between them is. Then we will start understanding a comparison between Azure Pipelines hosted agent and Azure Pipelines self-hosted or private agent from the configuration perspective.

Then we will talk about the comparison from the characteristics of each agent type, and when to use each one or each type. Also, we will understand when not to use each agent type. It's very important to have an implicit definition of when to use and when not to use it.

We will then understand the difference between Azure Pipelines organization pool and Azure Pipelines project pool, and the relationship between Azure DevOps projects, Azure Pipelines project pool, and Azure Pipelines organization pools. After that, we will understand how we can delegate Azure Pipelines organization pool admin to an Azure DevOps project admin.

For example, if you have an Azure DevOps organization and you are the main administrator and you don't want to give the organization administrator to the project admin, you can configure and manage the agent build pool. We will see how to delegate this permission for the project admin without delegating the organization admin after that we will understand the roles and the permissions for Azure Pipelines organization.

Next, we will start talking about the difference between Azure Pipelines agent running as a service and Azure Pipelines agent running as an interactive or a process. We will understand how to configure that and what the deep differences between them are. After that, we will see how to install Azure Pipelines for multiple agents on the same machine and how to uninstall or remove Azure Pipelines from a machine.

We will then talk about how to run Azure Pipelines agent as a service or as a process or interactive mode required to run automated UI testing. After that, we will see the demo workflow. As you may already be used to in my videos, I prefer to describe the demo steps in a workflow so you can understand exactly what will happen in the demo. 

In the first demo, we will get an understanding or get an overview of what the current Azure Pipelines hosted images by Microsoft are. In the second part of the demo, I will start creating an Azure DevOps organization pool and then an Azure Pipelines project pool for different projects with installation for Azure Pipelines for multiple agents on the same machine. Then creating Azure Pipelines project pool with auto-provision, the Azure Pipelines organization pool and then install the agent as an interactive or a process, trying to start and stop the agent or the interactive process. 

After that, we will see how to uninstall or remove Azure Pipelines agent from the machine.

>For more information about how to work with Kubernetes clusters and deploy them to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see [Kubernetes cluster for beginner](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/)
{: .prompt-tip }
{% include embed/youtube.html id='4DUhc0MjdUc' %}


## Azure Pipelines hosted agent vs self-hosted agent or private agent {#_Toc20854032}

![Azure Pipelines Hosted Agent VS. Self-Hosted Agent (Private)](/assets/img/2019/10/Hosted-Agent-VS.-Self-Hosted-Agent-Private-1024x578.png)

Azure Pipelines Hosted Agent VS. Self-Hosted Agent (Private)

So, Azure Pipelines hosted-agent is provided by Microsoft. They are provided as software-as-a-service. You just consume them, you don't have access to these servers, and you don't configure these servers.

On the other side, Azure Pipelines self-hosted agent is a private agent that could be on-premises because this could be your machine on your own premises or maybe your machine on the cloud at any cloud provider. You manage it, so you control everything about this machine.

>For more information about how to work with **Git** with animation. All commands will be represented in graphical animation. E.g. git branch, git merge, git rebase, git cherry-pick and many others, see [Mastering Git with animation](https://mohamedradwan-devops.github.io/posts/mastering-git-from-beginner-to-advanced-step-by-step-with-graphical-animation-commands/)
{: .prompt-tip }
{% include embed/youtube.html id='ZgCCnv9LxzA' %}


## Azure Pipelines configuration comparison

![Azure Pipelines Configuration Comparison](/assets/img/2019/10/Azure-Pipelines-Configuration-Comparison-1024x572.png)

If we look at the Azure Pipelines hosted agent, it's ready-made images. So, we have the operating system and the applications on each image. The current images are the following:

- Ubuntu 1604
- macOS
- macOS High Sierra
- Windows 2019 with VS2019
- VS2017 (Windows Server 2016)
- Hosted (Windows Server 2012 R2/old Visual Studio)
- Windows Container

In the hosted agent, you don't install either the operating system or applications on this machine. There is a build task that we can use to do some installation but that's another story: here is the link: <https://docs.microsoft.com/en-us/azure/devops/pipelines/process/tasks?view=azure-devops&tabs=yaml>

On the other side, with Azure Pipelines self-hosted agent, because we manage this machine, we are responsible for everything from the installation of the OS to the installation of all applications and configuration.

Of course, if this agent is a machine on the cloud, I may use a template with the operating system already installed. So, I don't install the operating system but if the agent machine is on-premises, it means that I will install everything.

## Azure Pipelines characteristics comparison

![Azure Pipelines Characteristics Comparison](/assets/img/2019/10/Azure-Pipelines-Characteristics-Comparison-1024x571.png)

If we look at the Azure Pipelines hosted agent, I don't need to worry about patches and updates because the hosted agent is provided as a service. I consume them; I don't manage them. So, I don't need to worry about any updates or patches for this machine.

It's a very quick way to get an agent with the desired operating system and configuration. For example, if I want to build an Android application and I need the macOS, it's a very quick way to get a build agent with macOS ready immediately to start building my application.

It's an amazing way to get a macOS agent on demand instead of having your own agent without the utilization of this machine. Imagine that if you have a machine in which you have a macOS that you are using as a build but because this is a building machine, you just reserve this machine for the build but you are not using it most of the time. So, by having a hosted build, it means that you utilize the time for this license because you are not consuming the license without need.

If you are using a macOS hosted agent and you are in Europe, you just need to consider and review the GDPR, because in the case of Azure Pipelines hosted agent for macOS, the data is stored in the USA. So, GDPR regulations may need to be revised to ensure compliance.

You can't change the hardware or software configuration. So, for example, if you want to increase the memory or change the hard disk to a super speed hard disk, you can't do that.

Azure Pipelines self-hosted agent: because you have responsibilities for the configuration of these machines, you start managing the operating system, installing the application, patches, and updates, and so on. You can change anything in the machine, so you can change the configuration, you may increase the memory or change the hard disk to speed up this machine.

>For more information about how to work with **Docker** like, pull docker image, run docker image and work with container, see [Docker for beginners](https://mohamedradwan-devops.github.io/posts/docker-for-beginners-step-by-step-tutorial/)
{: .prompt-tip }
{% include embed/youtube.html id='3RJv6yVfaRE' %}



## When to use Azure Pipelines hosted agent and when to use self-hosted agent {#_Toc20854035}

For the hosted agent, when you have a project that has a small size of source code, it doesn't take a long time to download because the hosted agent machine is created on the fly and torn down at the end of the build. Every time you run the build, it will download the source code. So if your source code is small, then you can use a hosted agent. If the code doesn't take a long time to compile, if your build process is optimized and your unit testing runs fast, for example, you follow the best practices for CI and all your unit tests run in memory, then they run very fast.

For self-hosted, I will say, always start with a hosted agent. Don't start with self-hosted and just promote to the self-hosted only if you have any issue with the hosted like performance, security, accessibility, etc.

Let me give you an example. If you remember when we design the class and we want to use private or public methods, we usually recommend making the method private. And if you need to provide it to be consumed by other classes, you promote it to the public. The same idea for Azure Pipelines: start with a hosted agent and promote that to self-hosted.

## Azure Pipelines Demo workflow 

![Azure Pipelines Demo work flow](/assets/img/2019/10/Azure-Pipelines-Demo-Workflow-1024x574.png)

### Azure Pipelines Demo workflow

- Create Azure Pipelines organization agent pool with name "BuildPool_1"
- Download Azure Pipelines agent and copy it to 3 folders.
- Install Azure Pipelines agent multiple times (Agent_1, Agent_2) on the same machine for organization agent pool "BuildPool_1"
- Create Azure DevOps project agent pool "BuildPool_1" for Project_1 that is mapped to existing organization agent pool "BuildPool_1"
- Create Azure DevOps project agent pool "BuildPool_1" for Project_2 that is mapped to the existing organization agent pool "BuildPool_1"
- Create Azure DevOps project agent pool "BuildPool_2" for Project_1 that will create a new organization agent pool "BuildPool_2"
- Install Azure Pipelines agent as a process or interactive for organization agent pool "BuildPool_2"
- Remove or uninstall Azure Pipelines agent

There are many details in the video. I recommend watching the video for better understanding.
