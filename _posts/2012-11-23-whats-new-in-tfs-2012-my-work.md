---
layout: post
title: "What's New in TFS 2012? My Work"
date: 2012-11-23 19:21:45 +0100
---

In this series, I will start introducing what\'s new in Visual Studio 11 and Team Foundation Server 11 (TFS 11), or as we expect to be [Visual Studio 2012](http://www.microsoft.com/visualstudio/11/en-us "Visual Studio 2012") and [Team Foundation Server 2012](http://msdn.microsoft.com/en-us/library/fda2bad5%28v=vs.110%29 "Application Lifecycle Management with Visual Studio and Team Foundation Server") (TFS 2012).

1.  [Introduction](https://mohamedradwan-devops.github.io/posts/whats-new-in-tfs-11-introduction/ "Introduction")
2.  [Project Management Tool](https://mohamedradwan-devops.github.io/posts/whats-new-in-tfs-2012-management-tool/ "TFS Management Tool")
3.  [SSDT (SQL Server Developer Tool)](https://mohamedradwan-devops.github.io/posts/whats-new-in-tfs-2012-ssdt-sql-server-developer-tool/ "SSDT (SQL Server Developer Tool)")
4.  [Team Explorer](https://mohamedradwan-devops.github.io/posts/whats-new-in-tfs-2012-team-explorer/ "Team Explorer")
5.  [My Work](https://mohamedradwan-devops.github.io/2012/11/23/whats-new-in-tfs-2012-my-work/ "My Work")
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

# **My Work**

A new Window introduced in [Team Foundation Server 2012](http://msdn.microsoft.com/en-us/vstudio/ff637362.aspx "TFS 2012").

#### The following is a step-by-step video that covers the entire topic.

{% include embed/youtube.html id='M_llrJ4mYj0' %}

**My work is like a Facebook feature.**

![MyWork-Facebook](/assets/img/2012/11/mywork-facebook.jpg "MyWork-Facebook")

For me, I think of this feature like the Facebook notification. It will enhance the interactivity between you and your team. Let\'s see the Facebook analogy: if any of your close friends adds a post or photo, this will appear in your notification. No need to check the wall every minute for new posts from your close friends. This is My Work, keeping you connected with what\'s going on without needing to check all the time. There is no need to query the work items to know if there are new tasks assigned to you, if your code review is completed, if you have new bugs, and many other options.

My Work depends on the login activity to determine what data to bring, retrieving all your data (Tasks, Pending Changes) based on your identity when you log into Team Foundation Server. My Work is based on a Task-Based Development Model to provide a very high synchronization mechanism with your teammates.

**My Work Sections**

![MyWork](/assets/img/2012/11/mywork-1.png "MyWork")

As we can see, My Work is divided into four sections:

- In Progress Work
- Suppressed Work
- Available Work Items
- Code Review

There will be separate posts for the **Suppressed Work** and **Code Review** sections. In this post, I will focus on **In Progress Work** and **Available Work Items** only.

**Available Work Items (section)**

![Available-WorkItems](/assets/img/2012/11/available-workitems-1.png "Available-WorkItems")

This is a Team Explorer section that retrieves data based on your identity and a work item query. You can open this query to get more information about the criteria that retrieve the data. You can also create new work items from the new menu.

**In Progress Work (section)**

![In-Progress-Work](/assets/img/2012/11/in-progress-work-1.png "In-Progress-Work")

This is a Team Explorer section that shows what you are currently working on. It could contain tasks, code pending changes, and it\'s very intelligent to show only what you can do at this moment. For example, if there are pending changes, it will show a check-in command; if not, it will not show it. If there are any project edits, it will show the suppress button.

**Drag and drop work items from available to in progress**

![Drag-and-Drop](/assets/img/2012/11/drag-and-drop2-1.png "Drag-and-Drop")

To start work on a task, you just select it and click start, or simply drag and drop it to the **In Progress Work** section. Remember, if you have **10 tasks** to do, you can only work on one task at any point in time. The idea here is to put one task inside the **In Progress Work** section that you will work on right now. It should have only one task at a time, making it very intelligent to associate the task when you try to check in your code. If you are not finished, the task should be associated; if you are finished, it should be closed.

**In Progress Work with and without pending change**

![MyWork-with-without-pending-change](/assets/img/2012/11/mywork-with-withoutpending-change-1.png "MyWork-with-without-pending-change")

**In Progress Work after clicking on check-in command**

![MyWork-with-without-pending-change-check-in](/assets/img/2012/11/mywork-with-withoutpending-change-check-in-1.png "MyWork-with-without-pending-change-check-in")

When we move the work item from the **Available Work Items** section into the **In Progress Work** section, this will change the state of the work item to in progress, and this can be shown on the **Team Web Access**. This applies when we click finish or check-in. However, the reverse is not true. If you change the work item on **Team Web Access** from **To Do** to **In Progress**, this will not reflect on My Work or **In Progress Work**.

**Change the work item to In Progress inside My Work reflects on Team Web Access**

![Move-to-InProgress](/assets/img/2012/11/move-to-inprogress-1.png "Move-to-InProgress")

**Change the work item to finish inside My Work reflects on Team Web Access**

![Finish-Task](/assets/img/2012/11/finish-task-1.png "Finish-Task")

**Change the work item to In Progress inside Team Web Access doesn\'t reflect on My Work**

![Move-task-onboard-don't-on-My-Work](/assets/img/2012/11/move-task-onboard-donton-my-work-1.png "Move-task-onboard-don't-on-My-Work")

**Links:**

- [Visual Studio Premium and Ultimate 2012: How to multi-task with My Work](http://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-How-to-multi-task-with-My-Work "Series Visual Studio 2012 Premium and Ultimate Overview")
- [Wrapping up TFS 11 Version Control improvements](http://blogs.msdn.com/b/bharry/archive/2011/09/01/wrapping-up-tfs-11-version-control-improvements.aspx?ocid=soc-n-eg-elite--MRadwan)
- [The New Team Explorer in TFS 11](http://blogs.msdn.com/b/bharry/archive/2011/09/19/the-new-team-explorer-in-tfs-11.aspx?ocid=soc-n-eg-elite--MRadwan)
- [Making Developers More Productive with Team Foundation Server 11](http://msdn.microsoft.com/en-us/vs11trainingcourse_makingdevsmoreproductive.aspx)
- [Why the task that In Progress doesn\'t appear in "In Progress section of the My work in Team Explorer 11"](http://social.msdn.microsoft.com/Forums/en-US/TFSvnext/thread/add93436-cf1a-4ad6-b019-f9e285048553 "Why the task that In Progress doesn't appear in 'In Progress section of the My work in Team Explorer 11")
