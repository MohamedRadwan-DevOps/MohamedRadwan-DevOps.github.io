---
layout: post
title: "Securing Your Application, Infrastructure, Environment Continuously in DevOps"
date: 2019-11-02 17:21:28 +0100
---

{% include embed/youtube.html id='VUi1LlAIRyc' %}

In this video, we will see how to secure your application infrastructure and the environment continuously in DevOps.

## Intro 

We are going to see a comparison between traditional security vs. DevSecOps, so we can see how the security model evolved to keep up with continuous delivery. Then we will start to look at how to treat security as a continuously varying state. We will see how the evolution of DevOps and the software development industry has brought a new paradigm shift. 

After that, we will talk about the relation between continuous practices and check the level so we can understand how shift left can affect the continuous practices. Then we will talk about security and compliance within [DevOps](https://azure.microsoft.com/en-in/services/devops/). 

After that, we will understand what we need to check for security to answer the question of what, and then we will answer the question of how to check for security. We will understand how we can achieve that. Then we will take an overview about OWASP (Open Web Application Security Project) and understand what products they produce to get more information about them. 

We will talk about an overview of the secure DevOps kit, which is an internal tool developed by Microsoft and shared with their customers. After that, we will discuss different types of scans using the security DevOps kit. Finally, we will talk about an overview of Azure Policy.

## Traditional development to agile and DevOps 

![Traditional-development-to-agile-and-DevOps](/assets/img/2019/11/Traditional-development-to-agile-and-DevOps-1024x544.png)
*Traditional-development-to-agile-and-DevOps*

We moved from traditional development to agile and DevOps, which means increasing the frequency of deployment in production. However, this business agility should not come at the expense of security. The question here is: Can the current security model and practices keep up? The answer is no, because the current security practices are not flexible enough to keep up with the changes. 

So it is important to stop treating security as a milestone and instead treat it as a continuous varying state. With this in mind and with continuous delivery, how do you ensure that your applications are secured and stay secure? How can you find and fix security issues early in the process? All of these practices are commonly referred to as DevSecOps.

>For more information about how to work with Kubernetes clusters and deploy them to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see [Kubernetes cluster for beginner](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/)
{: .prompt-tip }

## Security as a continuous varying state 

We are going to treat security as a continuous varying state. We should also implement [continuous assurance](https://azsk.azurewebsites.net/04-Continous-Assurance/Readme.html) as a part of our DevOps practices. 

One of the very important paradigm shifts in our software industry is the concept of shift left and shift right. Shift left is all about moving the practices that we usually do at the late stages in the process to be at the very beginning. For example, testing. By moving testing to be with development, we can help produce faster software with higher quality. But building quality from the beginning is not enough. We also need to shift right, which means getting data from production. The ability to monitor the application and get real-time data from production is very important.

## DevOps is better for security

![DevOps-is-better-for-security](/assets/img/2019/11/DevOps-is-better-for-security-1024x547.png)
*DevOps-is-better-for-security*

Talking about DevOps, we are not in the position to defend that DevOps is not bad for security. We go even further and see that DevOps is better for security. By moving fast, we become more secure because we are not standing in a vulnerable position for a long time. It's very simple: compliance relies on automation, which means that we are going to automate compliance by automating the pipeline and certifying the pipeline instead of certifying each release. This means switching the conversation with the security team to approve the pipeline, with the ability to monitor and audit all the processes at any point in time. Security needs to shift from the end to be evaluated at every step of the process. Securing the application is a continuous process.

>For more information about how to work with **Git** with animation. All commands will be represented in graphical animation. E.g. git branch, git merge, git rebase, git cherry-pick and many others, see [Mastering Git with animation](https://mohamedradwan-devops.github.io/posts/mastering-git-from-beginner-to-advanced-step-by-step-with-graphical-animation-commands/)
{: .prompt-tip }

## The risk of having OSS libraries 
Some of the risks of having OSS libraries or open-source vulnerabilities can be seen in the data breach report from Verzion. We can see that 85% of the vulnerabilities in the last year are the same as the top ten vulnerabilities from the previous years. This means that hackers are still targeting the top ten vulnerabilities due to a lack of awareness and practices.

The Common Vulnerabilities and Exposures (CVE) database is a platform aimed at collecting and maintaining information about discovered computer security vulnerabilities. For example, it will provide descriptions of the identified vulnerabilities, potential impact on affected systems, and any workarounds or updates to mitigate the issues. This common vulnerability and exposure database is a community effort.

The National Vulnerabilities Database (NVD) is another platform that depends on the common vulnerabilities database, but it is maintained or managed by the US government and provides enhanced information for the common vulnerabilities database.
