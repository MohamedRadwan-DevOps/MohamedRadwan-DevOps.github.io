---
layout: post
title: "Difference between Continuous Deployment and Release Management"
date: 2016-07-24 22:18:20 +0100
---

## Introduction 

In some previous post I've described what kind of methodology are **[DevOps](https://mohamedradwan-devops.github.io/posts/devops-framework-and-practices/)** and what are the main differences between **Development** and **Operations**. In this post I'm going to describe the main differences between **[Continuous Deployment](https://msdn.microsoft.com/en-us/library/ee308011(v=vs.100).aspx)** and **[Release Management](https://www.visualstudio.com/en-us/docs/release/getting-started/understand-rm)** and how does the absence of each of them interact with the other.

>You can see this vide, if you would like to find more information about a walkthrough introducing the Release Management and Build Automation using TFS 2017/2015. Step by step about all process, starting from creating the project. Check in the code in the source control, create a build definition and trigger the build. And also create a release pipeline. Learn how to configure properly the build steps, including Copy Files and Publish Build Artifacts. See how to create new release definition, add environments and link to build definition. Afterwards see how to add tasks to the release definition, like Windows Machine File Copy and configure it properly.
{: .prompt-info }

{% include embed/youtube.html id='vev3Czaa1pA' %}

## Part 1: Continuous Deployment DevOps Practice 

Pushing to production new versions of software under development is called **Continuous Deployment**. In big organizations, software is deployed thousands of times each day. **Continuous Delivery** involves some manual steps as in this practice the software is always release-ready, yet it is to be decided by the business personnel the timing of when to push it into production and so the final deployment is a **manual step**. On the other hand, everything is **automatic** with **Continuous Deployment**. Any updated working version of the application is automatically pushed to production. **Continuous Deployment** mandates **Continuous Delivery**, but the opposite is not required. In both cases **agility** is of the greatest importance, but **continuous delivery** allows businesses to manually decide when changes are implemented to applications and services. In an ideal world, **continuous deployment** would be adopted by the majority of companies. But sometimes due to some constraints this is not possible. And in some scenarios, the IT department must wait before a feature goes live, making **continuous deployment** unworkable.

![1-Continuous Deployment DevOps Practice](/assets/images/2016/07/1-Continuous-Deployment-DevOps-Practice.jpg "1-Continuous Deployment DevOps Practice")

>You can see this video, if you would like to find more information about how to get started with Release Management and its advantages. See how to create a build definition using CI/CD Tools for VSTS Extensions. (I will be using Package Extension and Publish Artifact tasks), and also using DevOps-VSTS-POC trigger in order to enable CI. all of that in order to be able to publish, share, install and query versions. You will see how to create release definition. Choose an artifact and configure source for the artifact and default version. See how to create different environments or clone the existing one. In my case I am going to create QA, Preproduction and Production environment. Each with one phrase and one task. See also how to configure Publish Extension task for each environment. See an end-to-end continuous delivery pipeline. Using VSTS extension with Build and Release Management.
{: .prompt-info }

{% include embed/youtube.html id='uGAcWLnSU0A' %}

## Part 2: Release Management DevOps Practice 

**Release Management** helps automate the deployment and testing of software in multiple environments. Using **Release Management**, we can either **fully automate** or **semi-automate** the delivery of our software. It is an essential element of **DevOps** that helps our team continuously deliver software to our customers at a faster pace and with lower risk. **Release Management** takes **Continuous Deployment** to the next level and allows you to automate the movement of your code from a build all the way to production.

![2-Release Management DevOps Practice](/assets/images/2016/07/2-Release-Management-DevOps-Practice.jpg "2-Release Management DevOps Practice")

>You can find more information about **DevOps** in the following post: [DevOps: The Three Stage Conversation - People, Process, Products](https://mohamedradwan-devops.github.io/posts/devops-the-three-stage-conversation-people-process-products/) which describes the basic principles of **DevOps**. This post will be especially helpful to those for whom DevOps is still a new concept. If you prefer a deeper view on this topic, have a look at the following guide: [quick guide about Basic Principles of DevOps](https://mohamedradwan-devops.github.io/posts/published-a-quick-guide-about-basic-principles-of-devops/), which presents an overview of [DevOps](https://www.visualstudio.com/vs/devops/) process and practices, describing "the big picture", while still maintaining the high level of detail.
{: .prompt-info }

## Conclusion

You could have **Continuous Deployment** without **Release Management**, you could have **Release Management** without **Continuous Deployment**. You could have an entirely **manual process**, without **continuous deployment** but you have a **release management** pipeline. Where you got a bunch of manual tasks that you execute, where you can see where things actually are. So even though **Continuous Deployment** is a **fully automated process** - absence of **Continuous Deployment** does not in any way mean absence of **Release Management**.

>In order to ensure [**Continuous Integration**](https://www.visualstudio.com/team-services/continuous-integration/), we need to use proper **deploying strategy**. Read more about deploying with Feature Branches and Feature Toggle in the following post; [Deploy from Branches with and without Feature Toggle](https://mohamedradwan-devops.github.io/posts/promoting-your-application-deployment-to-different-environments-from-branches-with-and-without-feature-toggle/).
{: .prompt-info }
