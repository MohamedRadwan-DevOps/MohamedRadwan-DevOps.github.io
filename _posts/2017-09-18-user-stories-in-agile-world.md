---
layout: post
title: "User stories in Agile world"
date:   2017-09-18 08:00:38 +0100
---

## Introduction

In some of my previous posts, I've been describing what [Agile](https://mohamedradwan.com/posts/quick-intro-to-agile/) is and the usage of some [Agile tools](https://mohamedradwan.com/posts/tfs-2015-agile-project-management/), from the high-level. In this post, I'll focus on an important unit of Agile software development process, which is **User Story**. User stories represent smaller units of work that need to be implemented in the sprint. Starting the project with the [**Agile methodology**](http://agilemanifesto.org/), you will start with the creation of **Product Backlog**, where you will be adding **Product Backlog Items (PBI's)** with descriptions usually written in user story format. This might seem like a simple job, but you would want to consider some basic rules and recommendations before starting to add the description of **PBI**.

>You can find more information about **DevOps** in the following post: [DevOps: The Three Stage Conversation - People, Process, Products](https://mohamedradwan.com/posts/devops-the-three-stage-conversation-people-process-products/) which describes the basic principles of **DevOps**. This post will be especially helpful to those for whom DevOps is still a new concept. If you prefer a deeper view on this topic, have a look at the following guide: [quick guide about Basic Principles of DevOps](https://mohamedradwan.com/posts/published-a-quick-guide-about-basic-principles-of-devops/), which presents an overview of the [DevOps](https://www.visualstudio.com/vs/devops/) process and practices, describing "the big picture", while still maintaining the high level of detail.
{: .prompt-tip }


## Definition of user story

Considering working with **Agile methodology**, a user story is a high-level description of the PBI's requirements in the **Product Backlog**. It has to be the right size, not too detailed and not too abstract, and it has to have just enough information that the development team can start with the estimation of implementation effort. A user story expresses the small piece of business value, deliverable in one sprint. Deliverable doesn’t mean just developing the **PBI** but also testing in the same sprint. So, it has to be small or big enough to be developed and tested in the same sprint. My high recommendation for the creation of **User Stories** would also be to make a meaningful, short, but yet explanatory title of the user story. Considering that we are developing a game, I would highly recommend avoiding **User story titles** in this format:

- Game rules
- Game characters
- Main menu

Rather than having such titles, I would personally prefer to use User Story titles, as follows:

- Develop basic game rules in xy format
- List all available game characters
- Display main menus in the navigation bar

Another example of the Agile backlog is shown in the image below. This backlog was built for e-commerce purposes, and you can understand from the image below that each PBI is a separate story, which means that it can be implemented without any dependencies on other PBI's.

![Backlog_PBIs Kanban board VSTS](/assets/images/2017/09/Backlog_PBIs-1.png)

[More Info]{.ion-info} If you want to know more about maintaining the backlog properly, you can visit the following post: [Key Tips For Maintaining Good Product Backlog in Agile and Scrum](https://mohamedradwan.com/posts/key-tips-for-maintaining-good-product-backlog-in-agile-and-scrum/). The post describes a way to efficiently organize the [backlog](https://docs.microsoft.com/en-us/vsts/work/backlogs/create-your-backlog) items, allowing you to understand the requirements better and providing you with a higher level of detail of what is actually expected from the work or delivery perspective.

## Format or a template for User Story

There are three very important questions we should consider covering when writing user stories:

![Format_User Story-how to write a user story](/assets/images/2017/09/Format_User-Story-1.png)

**1. Who?** We need to ask ourselves for whom we are building this product or service. Who will be the actors using this product or the service? **2. What?** What is it that we are actually building or what are the user’s needs for this product or service? **3. Why?** This question covers the goal of the feature that we are building. We need to ask ourselves why the user needs this feature and why we are building it. The user story needs to cover all three layers or questions so that the team understands for whom, what, and why they are building the features. In this way, the **team can focus on providing a business solution to solve users' problems**, rather than just writing the code. Although there is no official template that Agile uses or enforces, there is a common and widely used template to write a good user story, that uses the following form:

> ## *As a \<role\> I want \<something/function\> so that \<goal/benefit/value\>.*

>Read detailed explanations about all types of **Scrum and Agile meetings** (Sprint Planning, Stand-up, Grooming, [Sprint](https://docs.microsoft.com/en-us/vsts/work/scrum/sprint-planning) Review, Retrospective Meeting) in my past post [Types of meetings in Scrum and Agile](https://mohamedradwan.com/posts/types-of-meetings-in-scrum-and-agile/)
{: .prompt-tip }


### Let’s try to take a look at two different examples, using the same template for the same task:

Task: Implement Trello Integration with VSTS

A poor example of a user story, with an attempt to respect such a template would be:

> #### *As a user, I want VSTS to integrate with Trello so that I can see the team’s board.*

A better example of the same user story:

> #### *As a user, I want VSTS to integrate with Trello so that I can see on boards when certain events happen in my team project.*

In the example below, you’ll see the User Story in the PBI, which is part of an existing Product backlog. In the image, you’ll see the User Story in the Description field, and below the Description field, you’ll see the Acceptance Criteria field. Acceptance Criteria are another important part of User Story, but I will not cover them in this post. For now, just consider them as additional guidelines for User Story implementation.

![Work-item form for user story VSTS](/assets/images/2017/09/Implement-Trello-Integration-with-VSTS.png)

## Important concepts

A very important concept, which everyone writing user stories should consider, was developed by **Bill Wake** in 2003 and is known under the acronym **INVEST**. All well-formatted user stories respect the [**INVEST concept**](https://en.wikipedia.org/wiki/INVEST_(mnemonic)). **I - Independent** (Can the PBI stand alone, without any dependencies on another PBI?) **N - Negotiable** (Can it be changed and adapted without breaking any explicit instructions?) **V - Valuable** (Does it have value for the end user?) **E - Estimable** (Can the team estimate the size of it?) **S - Small** (Is it small enough to be designed, coded, and tested within the sprint?) **T - Testable** (Is testing possible from acceptance criteria and DoD?)

![Invest_Concept_Agile](/assets/images/2017/09/Invest_Concept_Agile-1.png)

>Read about basic guidelines that you need to consider when building a **product backlog** in the following post, [Requirements (Epic, Feature, User Story), Task Size and Estimation in Agile and Scrum](https://mohamedradwan.com/posts/requirements-epic-feature-user-story-task-size-and-estimation-in-agile-and-scrum/), and also about its maintaining and refinement of the product backlog in [Key tips for Maintaining good product backlog in Agile and Scrum](https://mohamedradwan.com/posts/key-tips-for-maintaining-good-product-backlog-in-agile-and-scrum/).
{: .prompt-tip }

## Most common mistakes or misconceptions

There are many details about how to write a good user story. As explained in previous lines of this post, it might seem very easy to write a user story, but many Product Owners, even those with good backgrounds and experience, make some of the most common mistakes, which lead in the opposite direction from what we want. Here are some of the most common mistakes:

- **Too detailed user stories**, where I believe that most of the Product Owners do this with very good intention, but in the end, they end up with huge business documentation, which is not at all what is needed in order to reach good business value for the customer or end user.
- **Technical tasks are not user stories.** In many of my projects, I saw examples where the developers are writing user stories for their own scenario, such as: "As a developer, I want to conclude the development of my code, so that I don’t need to come back to the same issue." This leads to having non-working software and back to the waterfall approach.
- **Filling the blank spaces in the template.** This is another issue that I’ve noticed while participating in different projects. People usually just want to finish their tasks and move on. Finishing the task as quickly as possible usually means having poor output, without including the business value and just trying to fill the template with anything, even if it makes no sense.

>In order to ensure [**Continuous Integration**](https://www.visualstudio.com/team-services/continuous-integration/), we need to use a proper **deploying strategy**. Read more about deploying with Feature Branches and Feature Toggle in the following post: [Deploy from Branches with and without Feature Toggle](https://mohamedradwan.com/posts/promoting-your-application-deployment-to-different-environments-from-branches-with-and-without-feature-toggle/).
{: .prompt-info}

## Conclusion

User stories might seem like a very small unit in the **Agile software development cycle**, but they hold a very big weight for delivering quality and valuable products to the customer or end users. In this part of development, as a good **Product Owner**, you would really want to consider putting in the good effort to produce a well-designed and quality backlog, containing just the right level of user stories details, as this will be your basis for producing what the business needs. It’s definitely not an easy task and you will need to have a good balance between sense and details. Please note that there are still many other important parts of a user story. This post is just describing the main points and guidelines on how to start writing good user stories, but there is even much more to it. When we start adding more details to the user stories in grooming sessions, we start to define acceptance criteria and even wireframes, which are not covered in this post. All these parts are also very important, and a good Product Owner should know them by heart. Thanks for reading and feel free to leave your feedback or questions in the comments section below!

>If you would like to know more about Azure deployments, have a look at the post [How to deploy to Azure using Team Services Release Management](https://mohamedradwan.com/posts/how-to-deploy-to-azure-using-team-services-release-management/). The post describes how Azure deployments are made easy by using Visual Studio Team Services (VSTS) Release Management. You will see a step-by-step tutorial on how to configure and deploy to Azure in Release Management, and, moreover, how to configure an end-to-end pipeline for deploying applications on Azure.
{: .prompt-tip }

