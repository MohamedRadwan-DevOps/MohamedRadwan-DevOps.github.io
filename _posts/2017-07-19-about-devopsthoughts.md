---
layout: post
title: "About DevOpsThoughts"
date:   2017-07-19 08:00:16 +0100
---

# About the project

**DevOpsThoughts** is a community initiative aimed to teach the best practices in [**DevOps**](https://mohamedradwan.com/posts/what-is-devops/) through a multi-platform application which targets a variety of technologies. **DevOps** is one of the most emerging topics of software development today as it improves the whole software development process, but unfortunately, there is no clear, detailed and explicit model to teach the best DevOps & Software Engineering practices on real world projects, this was the main problem that leads to **DevOpsThoughts** community establishment. **DevOpsThoughts** teaches the best practices on a series of real-world e-commerce projects, each of which is

- Named after an animal name (We love animals, who doesn\'t?)
- Built with a specific set of technologies
- Is a branch in the DevOpsThoughts E-Commerce repository

>You can see this video If you would like to find more information about an introduction and overview of a series of videos about Microsoft Dynamics development, including the overview of the Microsoft Dynamics CRM itself, installing Microsoft Dynamics 2016 on Azure VM and how to upgrade to Dynamics 365, how to develop Dynamics CRM plugin, how to debug Microsoft Dynamics CRM project, create and run unit tests using FakeXRMEasy and Microsoft Fakes, JavaScript and front end unit tests as well code quality using JSHint, also how to create and run UI and how to integrate all the practices as part of the CI/CD (Continuous Integration and Continuous Delivery).
{: .prompt-tip }
{% include embed/youtube.html id='rEJMBwuKY6Y' %}

Further, in the post, I\'ll present the first project in the series of **DevOpsThoughts** project, which was named **DevOpsThoughts Rabbit**. The project is available in the public repository on [**GitHub**](https://github.com/DevOpsThoughts) and to start the following commands need to be run and the BranchName should be replaced with the name of the branch you want to clone.

```shell
git clone https://github.com/DevOpsThoughts/E-Commerce.git -b BranchName 
cd E-Commerce
```

>You can find more information about **DevOps** in the following post: [DevOps: The Three Stage Conversation - People, Process, Products](https://mohamedradwan.com/posts/devops-the-three-stage-conversation-people-process-products/) which describes the basic principles of **DevOps**. This post will be especially helpful to those for whom DevOps is still a new concept. If you prefer a deeper view on this topic, have a look at the following guide: [quick guide about Basic Principles of DevOps](https://mohamedradwan.com/posts/published-a-quick-guide-about-basic-principles-of-devops/), which presents an overview of [DevOps](https://www.visualstudio.com/vs/devops/) process and practices, describing \"the big picture\", while still maintaining the high level of detail.

# DevOpsThoughts Rabbit

**DevOpsThoughts Rabbit** is the first project in **DevOpsThoughts Series**. It\'s an e-commerce website built with the following technologies:

- [ASP.NET MVC 5](https://docs.microsoft.com/en-us/aspnet/mvc/mvc5)
- [Microsoft SQL Server 2014](https://www.microsoft.com/en-us/download/details.aspx?id=42299)
- Modern UI Tools & Frameworks, Like Twitter Bootstrap & Font-Awesome

Below is the homepage for **DevOpsThoughts Rabbit**. 

![Homepage DevOpsThoughts Rabbit](/assets/images/2017/07/Homepage-DevOpsThoughts-Rabbit.png)

**Pages list Grouped by User Role:**

- Visitor
  - Homepage
  - Product List Page
  - Product Details Page
  - Shopping Cart (Check Out) Cascading Menu Sub Page
  - Shopping Cart (Check Out) Page
  - Login Page
  - Add/Edit Delivery Address Page
  - Order Complete Page
  - Order Confirmation email
  - Registration Page
- Member
  - Forget the Password
  - Display/Edit Account Info
  - Order List Page
  - Addresses List Page
  - Payment Page (Note#6)
  - Dashboard (Member Homepage)
- Vendor/Admin
  - Order List Page
  - Order Details Page
  - Edit Order Page
  - Add/Edit Product
  - Dashboard (Control Panel Home page)
- Miscellaneous
  - Confirmation Message (Sub Page)
  - Loading (Sub Page or image)
  - Notification, Error, Warning


>If you would like to know more about the best practices for [DevOps](https://www.visualstudio.com/team-services/devops/), Continuous Integration and Continuous Delivery, you can have a look at the following post: [Configure CI (Continuous Integration) and CD (Continuous Delivery Pipeline)](https://mohamedradwan.com/2017/12/29/develop-vsts-extension-and-configure-ci-continuous-integration-and-cd-continuous-delivery-pipeline/).
{: .prompt-tip }


# Development of the Project

This model was developed for learning purposes, so we had to make a precise plan for the whole development process, using [Scrum, User Stories and Behavior Driven Development (BDD)](https://www.visualstudio.com/en-us/docs/work/guidance/agile-process-workflow) we can simply put the plan into this list:
**User Story** is a description of a specific functionality from an end-user perspective. **Product Backlog Item** is a single unit of work, here we mapped each user story to a PBI, so a PBI is a user story plus acceptance criteria, priority and tags. **Test Cases**, which are very important in connection to Behaviour Driven Development (BDD) and in this project we have test cases written on three levels:

- Conceptual Test Cases
- Functional Test Cases
- Usability & Functional Test Cases

>You can see this video if you would like to find more information about the new tools and enhancements for Continuous Delivery (CD) and DevOps with Visual Studio 2017. See how to download and initiate the Continuous Delivery Tools for Visual Studio extension. Create a new team project on VSTS or connect to an existing project. Clone a project to a local Git repository, create a simple web application, and finally how to configure the CD extension. Allowing you to create a Build definition, run that Build, trigger a Release and complete app deployment to the cloud. The process of making changes to the CD and DevOps pipeline is also demonstrated. As well as managing Build failures with the help of the described extension.
{: .prompt-tip }
{% include embed/youtube.html id='I9OAqrAuJT4' %}

I\'ll explain the details of each level in the next blog post of this series.

### Use Case Scenarios:

Which represents a list of user actions and system\'s response to it. In DevOps Thoughts, each PBI was mapped to a single use case scenario, which consists from related PBI\'S, Main Actors List, the list of pre-conditions, basic and alternative flow and from post conditions of scenario. **Basic Mockups**, which are very basic UI representation used to deliver an abstract format of the expected to UI design to a UI developer from end-user or product owner perspective. **PhotoShop Designs (PSDs)**, which are based on the Test Cases, Basic Mockups and PBI\'s. **Website Components** (HTML, CSS and JavaScript), which are basically the source code for UI, together with all elements used in UI, such as images, icons and libraries. **Storyboarding**, which is showing an illustration of user interaction with application story. **Products Data**, which was added into the application for the purpose of displaying a real image of the application. All products are filled with code, title, description, category, brand, etc, in order to ensure the, the application meets the real criteria.

[Tip]{.ion-tip} If you are interested in developing a [Visual Studio Team Service extension](https://docs.microsoft.com/en-us/vsts/extend/overview), and you would like to know and to follow the best practices for DevOps, Continuous Integration and Continuous Delivery, - have a look at the following post, [Develop VSTS Extension and Configure CI (Continuous Integration) and CD (Continuous Delivery Pipeline)](https://mohamedradwan.com/posts/develop-vsts-extension-and-configure-ci-continuous-integration-and-cd-continuous-delivery-pipeline/).

# Conclusion

The project DevOpsThoughts was very carefully designed and developed as a community project with a purpose of teaching the best DevOps & Software Engineering practices on a real projects. In the next post of this series, I will explain more in detail about each step of the development process that has been used for this project. 


