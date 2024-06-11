---
layout: post
title: "Fix the 'You do not have permissions to see this view. Contact a system administrator CRM (Microsoft CRM)' error"
date: 2018-03-07 17:12:18 +0100
---

Usually, if I have a problem that takes some time to resolve, I blog about it to help other people who might have the same issue.

## After adding a new user to [**Dynamics 365**](https://dynamics.microsoft.com/en-gb/) (on-premises)

Despite assigning a System Administrator Role to it, a lot of information was still not available to this user, and the following error was appearing:

>You do not have permissions to see this view. Contact a system administrator CRM
{: .prompt-danger }

The image below demonstrates the process of assigning roles in **Dynamics 365**:

![Managing User Roles in Dynamics 365](/assets/images/2018/03/Managing-User-Roles-in-Dynamics-365-1024x619.png)

[Tip]{.ion-tip} If you would like to learn more about Microsoft Dynamics development, including the overview of the Microsoft Dynamics CRM itself, installing Microsoft Dynamics 2016 on Azure VM and how to upgrade to Dynamics 365, how to develop Dynamics CRM plugin, how to debug Microsoft Dynamics CRM project, create and run unit tests using FakeXRMEasy and Microsoft Fakes, JavaScript and front-end unit tests as well code quality using JSHint, also how to create and run UI and how to integrate all the practices as part of the CI/CD (Continuous Integration and Continuous Delivery), have a look at [**this post**](https://mohamedradwan.com/posts/devops-for-microsoft-dynamics/)

After some research, I realized that to solve the problem everything I needed to do was to change the **Administration** to:

- Read-Write
- License: professional

![Dynamics 365 - Administrating Client Access](/assets/images/2018/03/Dynamics-365-Administrating-Client-Access-1024x755.png)

I hope this helps!

>You can find more information about **DevOps** in the following post: [DevOps: The Three Stage Conversation - People, Process, Products](https://mohamedradwan.com/posts/devops-the-three-stage-conversation-people-process-products/) which describes the basic principles of **DevOps**. This post will be especially helpful to those for whom DevOps is still a new concept. If you prefer a deeper view on this topic, have a look at the following guide: [quick guide about Basic Principles of DevOps](https://mohamedradwan.com/posts/published-a-quick-guide-about-basic-principles-of-devops/), which presents an overview of the [DevOps](https://www.visualstudio.com/vs/devops/) process and practices, describing "the big picture", while still maintaining a high level of detail.
{: .prompt-info }

