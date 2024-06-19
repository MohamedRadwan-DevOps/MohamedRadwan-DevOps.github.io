---
layout: post
title: "What's New in TFS 2012? - Team Explorer"
date: 2012-11-21 03:58:14 +0100
---

In this series, I will start introducing what\'s new in Visual Studio 11 and Team Foundation Server 11 (TFS 11), or as we expect to be [Visual Studio 2012](http://www.microsoft.com/visualstudio/11/en-us "Visual Studio 2012") and [Team Foundation Server 2012](http://msdn.microsoft.com/en-us/library/fda2bad5%28v=vs.110%29 "Application Lifecycle Management with Visual Studio and Team Foundation Server") (TFS 2012).

1.  [Introduction](https://mohamedradwan-devops.github.io/posts/whats-new-in-tfs-11-introduction/ "Introduction")
2.  [Project Management Tool](https://mohamedradwan-devops.github.io/posts/whats-new-in-tfs-2012-management-tool/ "TFS Management Tool")
3.  [SSDT (SQL Server Developer Tool)](https://mohamedradwan-devops.github.io/posts/whats-new-in-tfs-2012-ssdt-sql-server-developer-tool/ "SSDT (SQL Server Developer Tool)")
4.  [Team Explorer](https://mohamedradwan-devops.github.io/posts/whats-new-in-tfs-2012-team-explorer/ "Team Explorer")
5.  [My Work](https://mohamedradwan-devops.github.io/posts/whats-new-in-tfs-2012-my-work/ "My Work")
6.  Code Review
7.  Suspend and Resume
8.  Local Workspace
9.  Pending Change
10. Diff and Merge tool
11. Unit Testing Improvement
12. Code Clones
13. Build Improvement
14. Storyboarding
15. Microsoft Feedback Client
16. Exploratory Testing Improvement
17. IntelliTrace in Production
18. Alerts
19. Administration

---

# Team Explorer

## What is Team Explorer?

As you may already know, there are many clients for TFS (Team Foundation Server) like Microsoft Excel, Microsoft Project, Team Web Access, and many other clients including Team Explorer. Team Explorer is considered the primary client for TFS. It is an add-in on [Visual Studio 2012](http://www.microsoft.com/visualstudio/11/en-us "Visual Studio 2012") or can be installed as a separate application. There are many changes, new and merged features in the new Team Explorer and Visual Studio 2012. For example, the Pending Change Window is merged within Team Explorer, and there are new windows added to Team Explorer, such as the new window called My Work, introduced in TFS 2012. In this post, I will focus on Team Explorer itself and delay any explanation of new or merged windows for upcoming posts. Any talk about new or enhanced features will be introduced as an example of the new capabilities of Team Explorer itself, which mostly apply to many other features.

## Team Explorer Enhancements

1. **Architecture (Web Based)**
    - Navigation and Extensibility
    - Work item search

2. **New and Merged Windows**

3. **On-Demand Data Retrieval (Paging)**

4. **Smart Commands and Context-Driven**

5. **Reducing Modality**

6. **Performance and Async Operations**

7. **Rollback in the UI**

#### The following is a step-by-step video that covers the entire topic.

{% include embed/youtube.html id='l0ZQB2JXZFM' %}

---

**1. Architecture (Web Based)**

- Navigation and Extensibility
- Work item search

**Old Team Explorer**

![Old-Team-Explorer-Architecture](/assets/images/2012/11/old-team-explorer-architecture2-1.png)

**New Team Explorer**

![Team-Explorer-2012-Architecture](/assets/images/2012/11/team-explorer-2012-architecture2-1.png)

The old version of Team Explorer was based on Tree/Nodes architecture, which was very limited for new extensions. Whenever an extension or feature was needed, the only way to add it was to add a new node, making the tree more complex than expected. In the new version, the architecture is based on a web navigation style. Team Explorer is like a main container with multiple pages, each page is a container with multiple sections, and each section carries one window with many commands.

![Team-Explorer-Architecture](/assets/images/2012/11/team-explorer-architecture.png)

There is a navigation bar to go home (main container) at any point in time, and there are back and forward buttons to move between pages and sections as you visit them. This architecture gives Team Explorer a richer extensible model, so we can extend it in the following ways:

- Add a new page to the navigation structure
- Add a new section to an existing page
- Add a top-level link to the Home page
- Add a secondary link beneath an existing top-level item on the Home page

**Work Item Search**

There is a work item search that allows us to search inside work items without needing a third-party tool. We expect this feature to become more complex in different releases of Visual Studio and TFS. There are some search syntax details available here: [Work Item Search Syntax](http://msdn.microsoft.com/en-us/library/cc668120.aspx "Work items search").

**2. New and Merged Windows**

![New Merged Window](/assets/images/2012/11/new-merged-window.png)

New windows have been introduced in TFS 2012, and some windows have been merged into Team Explorer. For example, My Work is a new window introduced in TFS 2012, and the Pending Change Window is merged into Team Explorer.

**3. On-Demand Data Retrieval (Paging)**

![On-Demand Data Retrieval](/assets/images/2012/11/on-demand-data-retrieval2-1.jpg)

In the old version of Team Explorer, when we opened a team project, we had to wait for all files to load and download (e.g., Reports, SharePoint documents). In this version of Team Explorer, nothing will be loaded until needed. It works like the paging concept when displaying many records. Once we request the next page, it connects and brings what we need.

**4. Smart Commands and Context-Driven**

![Smart Commands Context-Driven](/assets/images/2012/11/smart-commands-context-driven2-1.jpg)

There is a reduction in right-click commands by exposing them and making them intelligent. For example, the check-in policy violation section will not show up if there are no violations. If there are violations, it will appear. Many commands will not appear if there is no need for them.

**5. Reducing Modality**

![Reduce Modality](/assets/images/2012/11/reduce-modality2-1.jpg)

One of the things we really dislike is modal dialog boxes that show up and prevent us from doing anything else. There have been many improvements to reduce modality as much as possible. For example, the check-in pending change will not be modal anymore, so we don’t need to wait for all our files to be checked in before starting to use Visual Studio. Now, we can use Visual Studio while the code is being checked in.

**6. Performance and Async Operations**

To enhance performance, Microsoft has worked hard to move long-running tasks to background threads wherever possible. There are also many improvements in operation responses to achieve a responsive UI by increasing the number of Async Operations that interact with TFS, combined with the Reducing Modality feature, which introduces a very responsive UI.

**Old and already Async Operations:**

- History
- Annotate
- Source control explorer

**New Async Operations:**

- Checking in
- Editing a file
- Find shelveset
- Shelveset details and changeset details
- File compare
- Open the work item

**7. Rollback in the UI**

![Rollback 2](/assets/images/2012/11/rollback-2-1.png)

![Rollback 3](/assets/images/2012/11/rollback-3.png)

It’s no longer part of the Power Tool as a third-party library; it is now built-in.

**The project settings now also look different**

![Team Project Settings](/assets/images/2012/11/team-project-settings.jpg)

**Summary:** Team Explorer is one of the major changes in TFS 2012, with many new features and enhancements that cannot be covered in one or two posts. As a summary, Team Explorer offers a different experience with many changes. This post just highlights the main and significant changes of the new experience introduced in Team Explorer.

**Links:**

- [Wrapping up TFS 11 Version Control improvements](http://blogs.msdn.com/b/bharry/archive/2011/09/01/wrapping-up-tfs-11-version-control-improvements.aspx?ocid=soc-n-eg-elite--MRadwan)
- [The New Team Explorer in TFS 11](http://blogs.msdn.com/b/bharry/archive/2011/09/19/the-new-team-explorer-in-tfs-11.aspx?ocid=soc-n-eg-elite--MRadwan)
- [Making Developers More Productive with Team Foundation Server 11](http://msdn.microsoft.com/en-us/vs11trainingcourse_makingdevsmoreproductive.aspx)
- [Work Item Search Syntax](http://msdn.microsoft.com/en-us/library/cc668120.aspx "Work items search")
