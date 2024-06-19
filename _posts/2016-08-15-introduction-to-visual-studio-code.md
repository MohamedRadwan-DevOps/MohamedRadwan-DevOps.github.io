---
layout: post
title: "Introduction to Visual Studio Code"
date:   2016-08-15 22:07:09 +0100
---


### Introduction 

[**Visual Studio Code**](https://code.visualstudio.com/) is Microsoft\'s tool for source code editing and it is designed for **Windows**, **Linux** and **OS X**. It\'s a tool used as a support for embedded [**Git control**](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control), debugging, syntax highlighting, snippets, intelligent code completion and code refactoring. It is an agile, cross platform, and multi-language editor, which you can download directly from **[Visual Studio website](https://code.visualstudio.com/)**. 

![0-Visual Studio Code](/assets/images/2016/08/0-Visual-Studio-Code.jpg "0-Visual Studio Code")

>You can find more information about **DevOps** in the following post: [DevOps: The Three Stage Conversation - People, Process, Products](https://mohamedradwan-devops.github.io/posts/devops-the-three-stage-conversation-people-process-products/) which describes the basic principles of **DevOps**. This post will be especially helpful to those for whom DevOps is still a new concept. If you prefer a deeper view on this topic, have a look at the following guide: [quick guide about Basic Principles of DevOps](https://mohamedradwan-devops.github.io/postspublished-a-quick-guide-about-basic-principles-of-devops/), which presents an overview of [DevOps](https://www.visualstudio.com/vs/devops/) process and practices, describing "the big picture," while still maintaining a high level of detail.
{: .prompt-tip }


>If you want to know more about maintaining the backlog in a proper way, you can visit the following post: [Key Tips For Maintaining Good Product Backlog in Agile and Scrum](https://mohamedradwan-devops.github.io/posts/key-tips-for-maintaining-good-product-backlog-in-agile-and-scrum/). The post describes a way to efficiently organize the [backlog](https://docs.microsoft.com/en-us/vsts/work/backlogs/create-your-backlog) items allowing you to understand the requirements better, and providing you with a higher level of detail of what is actually expected from the work or delivery perspective.
{: .prompt-info }


### Overview of Visual Studio Code User Interface 

The main user interface of **Visual Studio Code** is divided into five sections:
1. Menu Bar
2. View Bar
3. Side Bar
4. Editor
5. Status Bar

![1-user interface of Visual Studio Code](/assets/images/2016/08/1.jpg "1-user interface of Visual Studio Code")

>The post [User stories in Agile world](https://mohamedradwan-devops.github.io/posts/user-stories-in-agile-world/) focuses on an important unit of Agile software development process 
{: .prompt-tip }

The post [User stories in Agile world](https://mohamedradwan-devops.github.io/posts/user-stories-in-agile-world/) focuses on an important unit of Agile software development process, which is [User Story](https://docs.microsoft.com/en-us/vsts/work/work-items/guidance/agile-process-workflow). The post also describes some basic rules and recommendations you have to follow before adding the descriptions of **PBI**.
{: .prompt-tip }


You can see this video, if you would like to find more information about what is the story behind containers and what drives or the needs it, we will know why companies moved from traditional solution architecture to Microservices and how this put containers as the perfect solution for running them, we will get quick intro to clear some definitions, tools, and keywords related to this ecosystem, for example, we will understand what is the difference between VM, Container, and Hyper-V Container, why we would prefer container over VM and when the VM is better.

We will understand the difference between container and image and know the life cycle of creating a new image and why I do that. Like adding more layers to the base image. Push that to container images registry on the cloud. Then pull that from the registry to anywhere to have a new container. Then it will understand how the orchestration and clustering work for containers by managing the underlying nodes which host the containers. That will understand also different technologies and services around container. Like Docker, Docker Hub, Docker Swarm, Kubernetes, Azure Container Services (AKS), Azure Container Registry.
{: .prompt-tip }
{% include embed/youtube.html id='18i94MfJSAI' %}

The first section at the top will be your menu bar, then on the extreme left-hand side you have got the view bar. Next to the view bar you have got the side bar and the big area in the center is where you have your editor and at the bottom there is a status bar.

### On the **menu bar** you have got a file menu.

The **file menu** will give you access to various file related functions so you can open files/folders, save files, close editor/folders etc. The edit menu will give you access to various basic editing functions such as undo, redo, cut, copy, paste and also the find and replace functions. On the **view menu** you can access and also toggle various of the user interface related components. So you can switch between various areas of the view bar. The go-to menu allows you to do basic navigation in your code so you can navigate forward, backward. Access the navigation history as well as go to a specific file, symbol, definition or a line number.

#### The **help menu** gives you access to the documentation and release notes and also check for updates.

The **view bar** on the left-hand side works in conjunction with the side bar. As you navigate between these various functional areas, you will also change the view of the sidebar. On the **status bar** you will be able to access various extension related functions. You will also see icons related to [**Git support**](https://git-scm.com/) so from here you can perform functionalities such as switching between branches and you can also synchronize changes in your local repository with your remote repository. Next to that there are **errors** and **warnings.** And that\'s going to be dependent on the type of project that you are editing. So if there are errors and warnings, you will be able to see those down here. On the right-hand side of the status bar, it shows **current line number** and **column**. It shows to us that we are using spaces or tabs and the number of spaces. It will show the encoding of the current file and then also it will allow us to set the end of line sequence. Smiley face allows you to tweet feedback to the visual studio code team. You can also submit a bug from here so this will take you to [**Visual Studio Code repository**](https://code.visualstudio.com/docs/editor/versioncontrol) on **GitHub** from where you can open an issue.

>You can see **[this video](https://www.youtube.com/watch?v=C0ecnvmdAuQ)**, if you would like to find more information about how to create Linux machine on Azure, we will select Ubuntu server and remote connect to it using Git bash and PuTTY, and we will see how to test that our connection is established using sudo command.
{: .prompt-tip }
{% include embed/youtube.html id='C0ecnvmdAuQ' %}

>In some of the previous posts you can find high-level descriptions of [Agile](https://mohamedradwan-devops.github.io/posts/quick-intro-to-agile/) principles and the usage of some [Agile tools](https://mohamedradwan-devops.github.io/posts/tfs-2015-agile-project-management/) and [Agile methodology](http://agilemanifesto.org/).
{: .prompt-info }

### Conclusion

Announcement and a release preview of **Visual Studio Code** were done on Microsoft\'s **[Build conference](http://news.microsoft.com/build2015/)** in 2015. Later in the same year, the release was done under the **MIT License**, the source code was posted to **[GitHub](https://github.com/)** and the announcement of extension support was done. In 2016 **Visual Studio Code** was released to the web and what is the best is that it is free, open source, and it runs everywhere no matter what OS you are using. There are many regular updates which are very easy to install and all updates are released on all platforms simultaneously.
