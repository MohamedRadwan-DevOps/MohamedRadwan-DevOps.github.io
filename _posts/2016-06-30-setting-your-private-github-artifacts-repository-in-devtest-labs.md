---
layout: post
title: "Setting your private GitHub artifacts repository in DevTest Labs"
date: 2016-06-30 15:05:00 +0100
---

### Introduction

In the previous post [Setting your private VSTS Git Artifacts repository in DevTest Labs](https://mohamedradwan-devops.github.io/posts/setting-your-private-vsts-git-artifacts-repository-in-devtest-labs/), I described the step-by-step process for setting up a private **VSTS Git Artifacts Repository**. You can set your private **Git Artifacts Repository** also by using a [GitHub Repository](https://github.com/Azure/azure-devtestlab). Usage of **Artifact Repository** enables you to completely automate the distribution and consumption of shared libraries. Usually, the common process for the manual update of a library starts when one developer builds and tests the library. Then the same developer drops the library in shared storage. After that, all other developers work on the code that occupies the library space, and they are even manually deploying the library to their workstations.

![1-The application Life Cycle GitHub DevTest Labs](/assets/img/2016/06/1-The-application-Life-Cycle-GitHub-DevTest-Labs.jpg "1-The application Life Cycle GitHub DevTest Labs")

**Automated library management** can save you a tremendous amount of time as it enables upstream library changes and quick implementation of that change in downstream code. This post will describe a step-by-step tutorial for setting your private artifacts repository by using a **GitHub Repository** in just four simple steps.

### Step 1-2: Setting the Name GitHub Artifacts Repository in the Lab 

Steps 1-2 are already described in the previous blog post [Setting your private VSTS Git artifacts repository in DevTest Labs](https://mohamedradwan-devops.github.io/posts/setting-your-private-vsts-git-artifacts-repository-in-devtest-labs/). You can follow them exactly as they are described in that blog post also for this case. Of course, you can use different names, but the process itself is the same.

### Step 3: Clone the URL from GitHub Repository 

**Azure DevTest Labs Community** is a public, community-contributed repository that allows the usage of **Azure Resource Manager** Quickstart Templates for **Azure DevTest Labs** and **Artifacts** for **Azure DevTest Labs** which can be deployed on a **Virtual Machine** in **Azure DevTest Labs** through the new **Azure portal**.
1. Click on the link [https://github.com/Azure/azure-devtestlab](https://github.com/Azure/azure-devtestlab) to access the **GitHub Repository**.
2. On the right side of the site, you will see the **Clone URL** option. Click on the **Copy** button to copy the link.

![3-Clone the URL from GitHub Repository](/assets/img/2016/06/3-Clone-the-URL-from-GitHub-Repository.jpg "3-Clone the URL from GitHub Repository")

### Step 4: Setting the Folder Path and Personal Access Token 

The **Folder Path** name is the name of the folder in your **Git Repository**. You will find more information about it in Step 1 of the blog post [Setting your private VSTS Git artifacts repository in DevTest Labs](https://mohamedradwan-devops.github.io/posts/setting-your-private-vsts-git-artifacts-repository-in-devtest-labs/).
1. Click on the **Personalized Access Token Icon**.
2. From the drop-down menu, choose **Settings**.

![4-1 Setting the Folder Path and Personal Access Token](/assets/img/2016/06/4-1-Setting-the-Folder-Path-and-Personal-Access-Token.jpg "4-1 Setting the Folder Path and Personal Access Token")

3. In the new window, the **Personal settings list** will open on the left side. From the list, choose **Personal Access Tokens**.
4. In the upper right corner, click on the **Generate new token icon**.
5. In the new window, type the **Token description**.
6. Click on the **Generate token icon**.

![4-2 Generate new token GitHub DevTest Labs](/assets/img/2016/06/4-2-Generate-new-token-GitHub-DevTest-Labs.jpg "4-2 Generate new token GitHub DevTest Labs")

7. In the new window, a **new Token** will be generated. Click on the **Copy** button to copy the **Token** to the **Personal Access Token** field in your **Lab**.
8. **Paste** the generated **Token** into the **Personal Access Token** field in your **Lab**.

![4-3 Copy Token into Personal Access Token field DevTest Lab](/assets/img/2016/06/4-3-Copy-Token-into-Personal-Access-Token-field-DevTest-Lab.jpg "4-3 Copy Token into Personal Access Token field DevTest Lab")

### Conclusion

**GitHub** is the place where you will find all kinds of software projects, from very simple programs to the most popular applications. It allows users to follow friends or even some famous developers from whom you want to learn or just see what they are working on. It is a perfect community where you can share your project to get feedback from the [GitHub community](https://community.github.com/) or share your project in a way that others can also use it. It is free for public usage and for open source projects. But for private repositories, their [paid plan](https://github.com/pricing) is very accessible.

>You can see this video, if you would like to find more information about how to import a Git Repository from one VSTS account/project to another VSTS account/project using the Import feature. See how to import into an existing repository or create a new one. Also, see how to create a personal access token to be able to import the repository.
{: .prompt-tip }

{% include embed/youtube.html id='4P7QW1C4bRo' %}

