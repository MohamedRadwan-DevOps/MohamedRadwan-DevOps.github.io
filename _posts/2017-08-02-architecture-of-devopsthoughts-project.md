---
layout: post
title: "Architecture of DevOpsThoughts Project"
date:   2017-08-02 08:00:13 +0100
---

In this third blog post about **DevOpsThoughts Project.** I\'ll present the **Architecture** and the **Project Layers** **Structure** used in the project. ++As the visualization is the best way to understand **DevOpsThoughts** architecture. I will present below a list of useful diagrams to explain the philosophy for their usage. 

>You can find more information about **DevOps** in the following post: [DevOps: The Three Stage Conversation - People, Process, Products](https://mohamedradwan.com/2016/10/31/devops-the-three-stage-conversation-people-process-products/) which describes the basic principles of **DevOps**. This post will be especially helpful to those for whom DevOps is still a new concept. If you prefer a deeper view on this topic, have a look at the following guide: [quick guide about Basic Principles of DevOps](https://mohamedradwan.com/posts/published-a-quick-guide-about-basic-principles-of-devops/), which presents an overview of [DevOps](https://www.visualstudio.com/vs/devops/) process and practices, describing \"the big picture\", while still maintaining the high level of detail.
{: .prompt-tip }


# Architecture Diagram

Architecture diagram is a graphical representation of System components and how they\'re (components) are grouped together. The **[UML Architecture Diagram](https://msdn.microsoft.com/en-us/library/dd409390.aspx)** gives use a general overview of how the system works and its principles. The architecture diagrams are usually presented on two levels:

- **High-level Design**, which gives the overall overview, with the description of the major components and it is showing the interaction between one another, in order to meet each requirement.
- **Design Patterns**, which are representing a certain approach to achieve a goal.


>You can see this video if you would like to find more information about an introduction and overview of a series of videos about Microsoft Dynamics development, including the overview of the Microsoft Dynamics CRM itself. Installing Microsoft Dynamics 2016 on Azure VM and how to upgrade to Dynamics 365, how to develop Dynamics CRM plugin, how to debug Microsoft Dynamics CRM project, create and run unit tests using FakeXRMEasy and Microsoft Fakes, JavaScript and front end unit tests as well code quality using JSHint, also how to create and run UI and how to integrate all the practices as part of the CI/CD (Continuous Integration and Continuous Delivery).
{: .prompt-tip }
{% include embed/youtube.html id='rEJMBwuKY6Y' %}


For anyone, working with [Visual Studio](https://msdn.microsoft.com/en-us/library/dd490886.aspx), the Architectural tool was unfortunately removed from [Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/modeling/what-s-new-for-design-in-visual-studio), but it can be still accessible with **Visual Studio 2015** and even still readable with **Visual Studio 2017**. ++So, if you are still using Visual Studio 2015, the tool allows you to create Architecture diagram models also in **Visual Studio** as a part of application or system\'s structure. So, I could say that **Architecture diagram** is some kind of a high-perspective plan or a map clarifying and communicating the ideas about the system structure and furthermore, explaining which user requirements must be supported by the system. Below is the **Architecture diagram** we have used in **DevOpsThoughts**.

![Architecture diagram](/assets/images/2017/07/Architecture-diagram.png)


>If you would like to know more about the best practices for [DevOps](https://www.visualstudio.com/team-services/devops/), Continuous Integration and Continuous Delivery, you can have a look at the following post: [Configure CI (Continuous Integration) and CD (Continuous Delivery Pipeline)](https://mohamedradwan.com/2017/12/29/develop-vsts-extension-and-configure-ci-continuous-integration-and-cd-continuous-delivery-pipeline/).
{: .prompt-info }


# Use Case Diagram

**Use Case Diagram** is [UML Diagram](https://msdn.microsoft.com/en-us/library/dd409432.aspx) used to represent different interactions with the system. Usually, they are also referred to as behavior diagrams, as they are explaining the set of use cases. Which will be performed together with external system or actor. Basically, they are capturing the dynamic or operating behavior of the system. In **DevOpsThoughts** we have used the **Use Case Diagram** also as an input for making **PBI\'s** and **User Stories** Below is the Use Case Diagram we have in DevOpsThoughts.

![Use Case Diagram](/assets/images/2017/07/Use-Case-Diagram.png)

>You can see this video, if you would like to find more information about the new tools and enhancements for Continuous Delivery (CD) and DevOps with Visual Studio 2017. See how to download and initiate the Continuous Delivery Tools for Visual Studio extension. Create a new team project on VSTS or connect to an existing project. Clone a project to a local Git repository, create a simple web application. And finally how to configure the CD extension, allowing you to create a Build definition. Run that Build, trigger a Release and complete app deployment to the cloud. The process of making changes to the CD and DevOps pipeline is also demonstrated. As well as managing Build failures with the help of the described extension.
{: .prompt-tip }
{% include embed/youtube.html id='I9OAqrAuJT4' %}


# Project Layers

**[Project Layers](https://msdn.microsoft.com/en-us/library/ee658109.aspx)** are usually used to present or develop the software design from the high-level perspective, in order to demonstrate how the software is structured into technical components. Furthermore, they show also how the functional components of the system are linked to the technical components and how the data is being treated. Below a screenshot from **Microsoft Visual Studio\'s Solution Explorer** for the different layers used in DevOpsThoughts.

![Project Layers](/assets/images/2017/07/Project-Layers.png)


>If you are interested in developing a [Visual Studio Team Service extension](https://docs.microsoft.com/en-us/vsts/extend/overview), and you would like to know and to follow the best practices for DevOps, Continuous Integration and Continuous Delivery, - have a look at the following post, [Develop VSTS Extension and Configure CI (Continuous Integration) and CD (Continuous Delivery Pipeline)](https://mohamedradwan.com/posts/develop-vsts-extension-and-configure-ci-continuous-integration-and-cd-continuous-delivery-pipeline/).
{: .prompt-tip }


# Conclusion

Diagrams are in general a very good representation of the components and information with visualization technique. For this reason, I decided also to present the architecture of the project **DevOpsThoughts.++** As it shows in a good visualized way the connections and interactions between different components.

>You can see this video, if you would like to find more information about how to use VSTS to manage some tasks for a small team, how to use a sprint as a backlog sprint, how to add tasks and what the appropriate characteristics of a task should be, how to review and remove tasks as a product owner, how to create sprints, how to manage task priorities, how to edit Capacity for each sprint, how to assign tasks to team members and how to assign tasks to different sprints.
{: .prompt-tip }
{% include embed/youtube.html id='uMk3KN7DXpk' %}
