---
layout: post
title: "Develop VSTS Extension and Configure CI (Continuous Integration) and CD (Continuous Delivery Pipeline)"
date: 2017-12-29 14:07:17 +0100
---

Visual Studio product team has done a great job developing [Visual Studio Team Service](https://www.visualstudio.com/vso/) and TFS to be extensible. They made it a complete platform for extensibility, bringing several ways to improve the current capabilities by developing extensions. This is why they provide a great [Marketplace](https://marketplace.visualstudio.com/vsts) where developers, either individuals or companies, can develop their extensions and publish them. 

If you are an individual or a company interested in developing [Visual Studio Team Service extensions](https://docs.microsoft.com/en-us/vsts/extend/overview) and would like to know and follow the best practices for **[DevOps](https://www.visualstudio.com/vs/devops/)**, Continuous Integration, and Continuous Delivery, this post is for you. You can look at more info about **DevOps** in my post, [DevOps: The Three Stage Conversation - People, Process, Products](https://mohamedradwan-devops.github.io/posts/devops-the-three-stage-conversation-people-process-products/) which will give you an idea about **DevOps** if it's new to you. If you would like more depth but still prefer the high level, you might look at my [quick guide about Basic Principles of Devops](https://mohamedradwan-devops.github.io/posts/published-a-quick-guide-about-basic-principles-of-devops/) which will give you an overview of **DevOps** and the big picture but still at a high-level view. 

I have created a video series on how to do that step by step as follows:

- [Part 0: Introduction and the table of content](#part-0-introduction-and-the-table-of-content)
- [1: How to create VSTS Publisher Id for Continuous Delivery](#part-1-how-to-create-vsts-publisher-id-for-continuous-delivery)
- [2: Develop your extension as a normal front end (SPA) HTML/CSS/JavaScript](#part-2-develop-your-extension-as-a-normal-front-end-spa-htmlcssjavascript)
- [3: Download and use VSS SDK for your VSTS extension](#part-3-download-and-use-vss-sdk-for-your-vsts-extension)
- [4: VSS manifest JSON file](#part-4-vss-manifest-json-file)
- [5: Package VSTS extension using TFS Command Line Interface tfx-cli](#part-5-package-vsts-extension-using-tfs-command-line-interface-tfx-cli)
- [6: Upload, share, and install VSTS extension](#part-6-upload-share-and-install-vsts-extension)
- [7: Configure Continuous Integration and Continuous Delivery Pipeline with VSTS](#part-7-configure-continuous-integration-and-continuous-delivery-pipeline-with-vsts)
- [8: Some errors and notes while creating VSTS extension and its Continuous Integration and Continuous Delivery](#part-7-configure-continuous-integration-and-continuous-delivery-pipeline-with-vsts)
- [Conclusion](#conclusion)

## Part 0: Introduction and the table of content

In this video, I give an overview of all the videos and connect all the videos together with the complete idea.

{% include embed/youtube.html id='uzQFvYY0xiM' %}

## Part 1: How to create VSTS Publisher Id for Continuous Delivery

To deploy extensions to the Visual Studio Team Service Marketplace, you need a Publisher Id. In this video, I explain how to do that, the difference between different Visual Studio Team Services publisher Ids (private and public, individual and company). For more info about that see this link: [Package, publish, unpublish, and install VSTS extensions](https://docs.microsoft.com/en-us/vsts/extend/publish/overview)

{% include embed/youtube.html id='uzQFvYY0xiM' %}

## Part 2: Develop your extension as a normal front end (SPA) HTML/CSS/JavaScript

The second part is how to develop the extension. In this video, I show how to do that with primitive languages. I mean just using JavaScript, HTML, and CSS. I didn’t even use TypeScript to show that you don’t need TypeScript or others, it’s just good practices.

{% include embed/youtube.html id='NdPKIllR5Iw' %}

## Part 3: Download and use VSS SDK for your VSTS extension

In this video, I show how to use the Visual Studio Services Web Extension SDK or VSS-SDK, which is just a JavaScript library to load our extension in Visual Studio Team Service (VSTS). I show how to reference it and how to use it inside your code. For more info about that see these links:
[https://github.com/Microsoft/vss-web-extension-sdk](https://github.com/Microsoft/vss-web-extension-sdk)
[https://www.npmjs.com/package/vss-sdk](https://www.npmjs.com/package/vss-sdk)

{% include embed/youtube.html id='Q8BVnDdcDvc' %}

## Part 4: VSS manifest JSON file

The VSS extension manifest file is a JSON file where we keep all the metadata about our extension, like the version, all the resources, CSS, images, JavaScript, etc. It also includes the logo, the publisher Id, and many others. For more info see the following link: [Extension manifest reference](https://docs.microsoft.com/en-us/vsts/extend/develop/manifest)

{% include embed/youtube.html id='GhwicJP9sw' %}

## Part 5: Package VSTS extension using TFS Command Line Interface tfx-cli

In this video, I show the next step. After we prepared all the resources, we just need to package the VSTS extension by putting all the files in one file with a VSIX extension. We need to download and install the TFS Command Line Interface (tfx-cli), a cross-platform command line tool that we can run on any platform. For more info about the command, you can find it here:
[https://www.npmjs.com/package/tfx-cli](https://www.npmjs.com/package/tfx-cli)

{% include embed/youtube.html id='i2LzbISRLiU' %}

## Part 6: Upload, share and install VSTS extension

In this video, I show how to upload the Visual Studio Team Service extension to the publisher Id and how to share it with a specific account and install it. This video is very important to understand the difference between private and public VSTS publisher Id and what it means to publish an extension to the VSTS Marketplace.

{% include embed/youtube.html id='0EZdEPfyBFI' %}

## Part 7: Configure Continuous Integration and Continuous Delivery Pipeline with VSTS

This video is the master scene of this series :) It explains the main idea of how to configure a Continuous Integration (CI) and Continuous Delivery workflow and pipeline. It shows how to implement some of the main and major practices of DevOps with Visual Studio Team Services Build and Release Management. It shows how to create a build definition and use build VSTS extension and publish the artifacts of the build, which will be available for Release Management. It also shows how to create a release definition and how to create different staging environments, and how to put tasks to automate the deployment including picking up the build and promoting it to different environments with request and approval process. If you would like to focus more on Release Management, you can look at my video [Release Management and Build Automation with TFS/VSTS](https://www.youtube.com/watch?v=vev3Czaa1pA&t=841s), which will give you a full end-to-end example of how to use Release Management.

{% include embed/youtube.html id='vGWaJWkTmF4' %}

## Part 8: Some errors and notes while creating VSTS extension and its Continuous Integration and Continuous Delivery

In this video, I show some of the issues I faced and how to fix them. It's better to show a quick fix for some errors as maybe you will face the same issues.

{% include embed/youtube.html id='Z6E-7v3NFjM' %}

## Conclusion

This post explains how to develop VSTS extension and how to configure a Continuous Integration (CI) and Continuous Delivery pipeline, but we can still take the whole principles with developing any other application. At the end, the tool is just an implementation of the concept behind the idea (practices) and VSTS is the best tool to implement software practices :-) Happy VSTS and Happy DevOps :-) 

Good links:
[Publishing Extensions for Visual Studio Team Services](https://www.youtube.com/watch?time_continue=134&v=PcuIWQToQBI)
[Extend Visual Studio Team Services](https://www.visualstudio.com/team-services/extend/)
[What are extensions?](https://docs.microsoft.com/en-us/vsts/extend/overview)
