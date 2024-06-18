---
layout: post
title: "DevOpsThoughts Rabbit"
date:   2017-07-26 08:00:16 +0100
---

# Introduction

As already explained in the first post of this series **About DevOpsThoughts**, which describes the basic idea behind the project and provides a higher perspective of it, the **DevOpsThoughts Rabbit** is the first project in the **DevOpsThoughts Blog Post Series**. It represents an e-commerce website, which was built using different technologies, such as [**ASP.NET MVC 5**](https://docs.microsoft.com/en-us/aspnet/mvc/mvc5), [**Microsoft SQL Server 2014**](https://www.microsoft.com/en-us/download/details.aspx?id=42299) and **Modern UI Tools & Frameworks**, like **Twitter**, [**Bootstrap**](http://getbootstrap.com/) & [**Font Awesome**](https://social.msdn.microsoft.com/Profile/mohamed.radwan-mvp/extensions). Further in this post, I'll describe in more detail all the development steps that were considered and implemented in the process of the project creation.

# User Stories & Product Backlog Items (PBIs)

A **User Story** is a description of specific functionality from an end-user perspective. A **Product Backlog Item** is a single unit of work. Here we mapped each user story to a PBI, so a PBI is a user story plus acceptance criteria, priority, and tags.

>The post [User stories in Agile world](https://mohamedradwan-devops.github.io/posts/user-stories-in-agile-world/) focuses on an important unit of the Agile software development process, which is [User Story](https://docs.microsoft.com/en-us/vsts/work/work-items/guidance/agile-process-workflow). The post also describes some basic rules and recommendations you have to follow before adding the descriptions of **PBI**.
{: .prompt-tip }


For each user story, we develop a Product Backlog Item (PBI), assign proper tags to it based on publicity (Public/Private), the main actor (Visitor/Member/Vendor/Admin), and workflow type (Basic/Advanced). Then we add its Acceptance Criteria. Each Acceptance Criteria consists of two main parts:

- **Action Criteria**: The options available for use and the system's response to them.
- **Input Validation Criteria**: Used only when there is an input form being used to clarify each input type, boundaries, and importance.

All PBIs are made on two levels:

- **Initial PBIs**: Contains each PBI's Title, Order, Tag, and Description (Description is the user story).
- **Detailed PBIs**: Contains the initial PBIs' content with enhancements to maintain consistency, plus the acceptance criteria.

All BWF PBIs are added to the source control in plain text format, so we can quickly trace any changes to it. Below is a sample for Vendor's login Initial PBI.

![Initial PBI](/assets/images/2017/07/Initial-PBI.png)

### Another sample for Vendor's login Detailed PBI.

![Detailed PBI](/assets/images/2017/07/Detailed-PBI.png)

>Read about basic guidelines that you need to consider when building a **product backlog** in the following post: [Requirements (Epic, Feature, User Story), Task Size and Estimation in Agile and Scrum](https://mohamedradwan-devops.github.io/posts/requirements-epic-feature-user-story-task-size-and-estimation-in-agile-and-scrum/). Also, read about maintaining and refining the product backlog in [Key tips for Maintaining good product backlog in Agile and Scrum](https://mohamedradwan-devops.github.io/posts/key-tips-for-maintaining-good-product-backlog-in-agile-and-scrum/).
{: .prompt-info }

# Test Cases

Test Cases are very important for Behavior-driven development (BDD). In **DevOpsThoughts**, we have test cases written on three levels:

1. **Conceptual Test Cases**

   Conceptual Test Cases are the most abstract form of test cases made with conceptual input only for the purpose of conceptualizing the flow itself.

2. **Functional Test Cases**

   Functional Test Cases are made for testing the application functionality without discussing UI elements or UX. They just ensure the application outputs the suitable output when some input is provided.

3. **Usability & Functional Test Cases**

   Usability & Functional Test Cases are the most detailed test cases. They care not only for functionality as functional test cases do, but also for the way the application responds to user actions from a user experience (UX) and user interface (UI) perspective.

# Use Case Scenarios

A Use Case Scenario is a list of user actions and system responses to them. In DevOpsThoughts, we map each PBI to a single use case scenario. Each scenario has the following:

- **Related PBI**: The related PBI name & Id.
- **Main Actors List**: A list of all actors involved in the specified use case.
- **Pre-conditions**: A list of all conditions that must be met before the use case starts in order for the use case to be valid. Example: Vendor has been logged into his account.
- **Basic Flow**: Sometimes called Happy Path, is the normally expected flow for the use case with the default system settings, where the use case is expected to succeed as per main actors' expectations.
- **Alternative Flows**: If available, alternative flows of a use case are the flows where main actors' expectations are not met yet.
- **Post-conditions**: A list of all conditions that must be met after the use case ends in order for the use case to be valid, example: Order was saved in the application.

Use case scenarios are divided into Initial and Detailed use case scenarios.

- **Initial Use Cases**: Have the above structure but with more abstraction, so not much attention is given to the details. It's used to make simple process outlining.
- **Detailed Use Cases**: Have the same structure as the initial use cases but with more details, like the input/output information and available user controls.

Below is a sample for Display Products List Initial Use Case Scenario.

![Initial Use Case Scenario](/assets/images/2017/07/Initial-Use-Case-Scenario.png)

### Another sample for Display Products List Detailed Use Case Scenario.

![Detailed Use Case Scenario](/assets/images/2017/07/Detailed-Use-Case-Scenario.png)

# Basic Mockups

Mockups are very basic UI representations used to deliver an abstract format of the expected UI design to a UI developer from an end-user or product owner perspective.

**Making Mockups** Mockups are usually made using a basic photo editing application like MS Paint or Paint.NET.

**Level of Details** Mockups usually represent only an abstract view of a web page, only spaces occupied and by which elements, and don’t include icons, content, or colors.

# PhotoShop Designs (PSDs)

Based on Test Cases, Basic Mockups, and PBIs, the final PSDs are made for the Project. A PSD file is a Photoshop Design file that can be edited later. PSD files are kept up-to-date with any modifications made to the UI.

**Level of Details** PSD Designs are made while keeping attention to details. We can logically view the Basic Mockups as initial designs, while the PSDs are the detailed designs. Below is a sample for the Final PSD Design for the homepage, and it is identical to the screenshot for the homepage at the very beginning of this readme file.

![Final PSD Design for the homepage](/assets/images/2017/07/Final-PSD-Design-for-the-homepage.png)

# Website Components (HTML, CSS, and JavaScript)

Website components are simply the source code for UI, alongside any elements used in the UI such as images, icons, and libraries. The Website components aren’t only used for Rabbit but are also used for other versions of the project that use the web as a presentation layer. Developing the website components uses PSDs as input. Each PSD is converted as it is to be a separate web page. We gave much importance to utilizing and minifying all of the UI source files. After each PSD is converted, it is reviewed on two levels:

- **External**: Ensuring the web page matches 100% with the provided PSD.
- **Internal**: Checking for source code quality, readability, and if the code is minified.

>You can see this video, if you would like to see a walkthrough to know more information about how to develop a VSTS Extension and how to configure Continuous Integration and Continuous Delivery Pipeline. Described the agenda of the next series of videos. Learn how to deploy from different environments using different Publisher IDs and VSTS accounts. Additionally, I will show how to develop a Single Page Application using HTML/CSS/JavaScript as a Front End developer. Also, learn how to download the VSS-SDK JavaScript Library and how to use it and its manifest file (vss-extension.json). Afterwards, I will pack the code into a VSIX package using the TFS command line, upload it, share and install it on a VSTS account. At the end, I will configure Continuous Integration and Continuous Delivery Pipeline and discuss errors you may face during this process, sharing some notes.
{: .prompt-tip }
{% include embed/youtube.html id='uzQFvYY0xiM' %}

# Storyboarding

Storyboarding is an illustration of a user interaction with an application story. Not to be confused with user stories! In storyboarding, we use visual images arrayed together for user interaction with the application to represent. Storyboards are easier to remember than other written Test Cases as they show the real UX, not just some text about it. In DevOpsThoughts, we use [Microsoft Office's PowerPoint](https://products.office.com/en/powerpoint) which allows developers to quickly make an animated representation of User interaction with application UI with higher quality. If we look at the PSDs and Basic Mockups as a User Interface representation, we should consider Storyboarding to be the User Experience Representation.

# Conclusion

This post, as the second one in the blog post series about the **DevOpsThoughts Project**, covers many details from the project development perspective. It explains for which purpose certain steps were developed, but it does not explain yet how they were developed and used in this project. The next post in this series will cover the **Design and Architectural point** of view of the project.
