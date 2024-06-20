---
layout: post
title: "Codeflyers Project"
date: 2016-07-15 02:05:04 +0100
---

### Introduction 

>If you want to know more about maintaining the backlog in a proper way, you can visit the following post: [Key Tips For Maintaining Good Product Backlog in Agile and Scrum](https://mohamedradwan-devops.github.io/posts/key-tips-for-maintaining-good-product-backlog-in-agile-and-scrum/). The post describes a way to efficiently organize the [backlog](https://docs.microsoft.com/en-us/vsts/work/backlogs/create-your-backlog) items allowing you to understand the requirements better, and providing you with a higher level of detail of what is actually expected from the work or delivery perspective.
{: .prompt-tip }

>Read detailed explanation about all types of **Scrum and Agile meetings** (Sprint Planning, Stand-up, Grooming, [Sprint](https://docs.microsoft.com/en-us/vsts/work/scrum/sprint-planning) Review, Retrospective Meeting) in my past post [Types of meetings in Scrum and Agile](https://mohamedradwan-devops.github.io/posts/types-of-meetings-in-scrum-and-agile/).
{: .prompt-info }

### What is Codeflyers Project? 

The **Codeflyers** project is a community project for building **applications** that target different platforms as much as possible. Involving all roles and stages of Software Development Life Cycle (**SDLC**). In order to provide a road map for how to implement **new** **and** **different** **technologies along with the process** **and provide **learning** perspectives. A few of the project roles include web design, web development, desktop development. Build engineering and deployment engineering along with positions for product owner and scrum master. The stages of **software development** included in the project are analysis, design, development, testing, deployment, monitoring and maintenance. To provide **learning materials**, outputs such as videos and step-by-step materials will be produced throughout the project. One of the ultimate goals of the Codeflyers project is to provide **comprehensive training** that covers all primary and alternative scenarios for realistic situations that may be encountered. As well as the opportunity for the community to apply the training in projects.

>The post [User stories in Agile world](https://mohamedradwan-devops.github.io/posts/user-stories-in-agile-world/) focuses on an important unit of Agile software development process, which is [User Story](https://docs.microsoft.com/en-us/vsts/work/work-items/guidance/agile-process-workflow). The post also describes some basic rules and recommendations you have to follow before adding the descriptions of **PBI**.
{: .prompt-info }

>Read about basic guidelines that you need to consider when building a **product backlog** in the following post, [Requirements (Epic, Feature, User Story), Task Size and Estimation in Agile and Scrum](https://mohamedradwan-devops.github.io/posts/requirements-epic-feature-user-story-task-size-and-estimation-in-agile-and-scrum/), and also about its maintaining and refinement of product backlog in [Key tips for Maintaining good product backlog in Agile and Scrum](https://mohamedradwan-devops.github.io/posts/key-tips-for-maintaining-good-product-backlog-in-agile-and-scrum/).
{: .prompt-info }

### Codeflyers Project: The E-Commerce Website 

As a starting point of the project, an **e-commerce website** has been developed as a base platform to apply training and lessons, and can be found at [https://github.com/codeflyers](https://github.com/codeflyers). To work on developing the site, there are documented **Product Backlog Items**, **Features**, and **Epics** to review and implement to make the project operational. *Note that the e-commerce site is simply a place to implement the training and create a functional application, not to actively sell products*. The current web design is primitive and just to produce the initial idea but I am working on a new and modern design, I finished the main idea but it still under enhancement and not finalize yet. The following is the home page for the new design.

![Codeflyers E-Commerce Site](/assets/images/2016/07/Codeflyers-Feature-Image.jpg "Codeflyers E-Commerce Site")

Here also some 

![Codeflyers-products4](/assets/images/2016/07/Codeflyers-products4.jpg "Codeflyers-products4")

Here is the old and the current design on GitHub 

![Codeflyers-old](/assets/images/2016/07/Codeflyers-old.jpg "Codeflyers-old")

### Product Backlog Items and Organizational Hierarchy

With larger projects, it is often more manageable to approach development in a piece-by-piece approach. Product Backlog Items (**PBIs**) on the backlog are tasks to complete on the e-commerce platform/website. Such as implementing search filters or updating an offer for a product. PBIs are comprised of smaller individual **tasks.** Such as developing a section of code that contributes towards achieving the overall output of a given PBI. Above PBIs in the organizational hierarchy is Features; **Features** are a collection of PBIs that contribute towards a facet of the project. At the top of the hierarchy is **Epics**, which are a collection of Features.

![Codeflyers PBI Backlog](/assets/images/2016/07/Codeflyers-Backlog-1.png "Codeflyers PBI Backlog")


>If you are in a situation when you need to integrate two backlogs, read the step-by-step post about [Two Backlog Integration](https://mohamedradwan-devops.github.io/posts/trello-vsts-integration/) in which I am providing a detailed description of the integration between [**Trello**](https://trello.com/) and [**VSTS**](https://www.visualstudio.com/team-services/) using [Zapier](https://zapier.com/).
{: .prompt-tip }

>There are many [**VSTS extensions**](https://marketplace.visualstudio.com/vsts) designed to make the work process easier. One of them is the **Delivery Plans** extension providing a better cross-team visibility. Read more about it in my post [Delivery Plans Extension for VSTS](https://mohamedradwan-devops.github.io/posts/delivery-plans-extension-for-vsts/) and learn how to manage more than one team in a much easier way.
{: .prompt-info }

### Best Practices

As a rule of thumb, **effective organization** is what allows large projects and community projects to function smoothly. To do this, Codeflyers has placed a time expectation based on the level of the contribution. Individual **tasks** should be measured in hours. PBIs should be measured in days. Features should be measured in weeks, and **Epics** should be measured in months. Likewise, to keep the project manageable and running smoothly. An average of tasks should be maintained to keep the project from being overwhelming. Each Feature should have between 3 and 5 PBIs, and each Epic should contain between 3 and 5 Features.

### Conclusion 

**Codeflyers** is a community project designed to teach practical skills for various roles in a software team. And provide opportunities to apply the knowledge in a practical setting. The layout of the project has made it simple to begin working on it and manageable. So that it will not become overwhelming initially or as time goes on. Codeflyers will be an ongoing project, regularly creating new content for training and continuously creating new projects as each finishes. The project can be found on [GitHub](https://github.com/)at [https://github.com/codeflyers](https://github.com/codeflyers).

>You can see this video, if you would like to find more information about the new tools and enhancements for Continuous Delivery (CD) and DevOps with Visual Studio 2017. See how to download and initiate the Continuous Delivery Tools for Visual Studio extension. Create a new team project on VSTS or connect to an existing project clone a project to a local Git repository. Create a simple web application and finally how to configure the CD extension. Allowing you to create a Build definition, run that Build, trigger a Release and complete app deployment to the cloud. The process of making changes to the CD and DevOps pipeline is also demonstrated. As well as managing Build failures with the help of the described extension.
{: .prompt-info }

{% include embed/youtube.html id='I9OAqrAuJT4' %}

>You can see this video, if you would like to find more information about Visual Studio Code, which is part of the Visual Studio family. The marketplace for the supported extensions is demonstrated as well as the process of installing. Disabling and reloading the extensions, and starting a new project - a new console application - and debugging this new project.
{: .prompt-info }

{% include embed/youtube.html id='GWdGSsUxkHE' %}
