---
layout: post
title: "Agile Portfolio Management in Team Foundation Server 2013"
date: 2013-09-28 00:24:48 +0100
---

The next Visual Studio and TFS is coming soon ([November 2013](https://mohamedradwan-devops.github.io/posts/visual-studio-2013-will-be-released-in-november-13-2013/ "Launch of Visual Studio 2013")) but most of TFS features is already there for TFS Service (Cloud). Agile Portfolio Management is a wonderful feature that gives the Portfolio or Program Managers all they need to manage multiple projects under one big project. So what did this feature introduce and how? This feature was introduced by two concepts:

1. The new usage of **Areas** and **PBI** (Product Backlog Item) behavior
2. Features (High-Level Requirement of the **PBI**)

### The new usage of **Areas** and **PBI** (Product Backlog Item) behavior

![Agile Portfolio Management TFS 2013 - 3](/assets/images/2013/09/agile-portfolio-management-tfs-2013-3.jpg)

In the previous image, we can see that in **[TFS 2012 (Team Foundation Server 2012)](http://msdn.microsoft.com/en-us/vstudio/ff637362.aspx "Team Foundation Server 2012")**, it supported the **Management Team** or any other naming role responsible for managing the output of a specific team. The **Management Team** would review and monitor the project from a team perspective, but it didn’t provide a **Project Perspective** which is provided now by **[TFS 2013 (Team Foundation Server 2013)](http://msdn.microsoft.com/en-us/vstudio/ff637362.aspx "Team Foundation Server 2012")**.

- **How did this happen?**

In the previous version of **[TFS 2012 (Team Foundation Server 2012)](http://www.microsoft.com/visualstudio/eng/products/2013-editions "Team Foundation Server 2012")**, if you just change the state of **PBI** (Product Backlog Item) to **Commit**, it will disappear from the [**Backlog**](http://msdn.microsoft.com/en-us/library/ee518933.aspx "product backlog") and you will only be able to see it when you access the [**Team**](https://mohamedradwan-devops.github.io/posts/whats-new-in-tfs-2012-management-tool/ "What is the team feature?") that works on that **PBI** but you don’t have a view of all **PBIs** across multiple teams.

- **How to support this view level?**

Create a new team project. In my case, I created (**Radwan Project**), open **Web Access** and go to **Settings**, add all the **Teams** that you want and leave the default team that is created with the project (**Radwan Team**). It will appear bold to indicate that it is the default team. This team will hold the **Portfolio, Program or the high-level Managers** that want to see the **Project Perspective**, see the following image.

![Teams](/assets/images/2013/09/teams-1.jpg)

Start adding the **Portfolio, Program or the high-level Managers** members to the default team (**Radwan Team**) and adding the other members to the other teams.

![Team Members](/assets/images/2013/09/team-memebers.jpg)

Go to **Areas** and start adding your needed areas. I added some modules and each module has two parts, part-1 and part-2. Choose areas for each team and choose the default area (**Radwan**) with the **sub-areas are included** option for the **Management team** which is the default team (**Radwan**). Now, any requirement added to any area of the project will be available for the **Management team**.

![Areas](/assets/images/2013/09/areas.jpg)

Go to **Iterations** and start assigning **Sprint 1** to all Teams (**Default, Team 1, Team 2, Team 3**).

![Sprint to teams](/assets/images/2013/09/sprint-to-teams.jpg)

Add your project requirements or **PBI** (Product Backlog Item) to your project, and assign them to **Sprint 1**. You will notice that even the committed **PBIs** have not disappeared from the **Backlog** view. [Note: I intend to not adding Features (High-Level Requirements) to explain that it is not the one that is responsible for the **Project Perspective** view.]

![PBIs](/assets/images/2013/09/pbis.jpg)

Notice also that the Management team can view the tasks inside the Backlog by choosing **View -> Tasks**.

![Task View in TFS 2013](/assets/images/2013/09/task-view-in-tfs-2013.jpg)

The view is also available for the **Sprint** as well.

![Sprint](/assets/images/2013/09/sprint-1.jpg)

Assign the **PBIs** for **Teams** using the areas as follows:

- PBI 1 and PBI 2 for Team 1
- PBI 3 for Team 2
- PBI 4, PBI 5, and PBI 6 for Team 3

The following image shows how **Team 1** sees the **Backlog**.

![Team1 PBIs](/assets/images/2013/09/team1-pbis-1.jpg)

The following image shows how **Team 2** sees the **Backlog**.

![Team2 PBIs](/assets/images/2013/09/team2-pbis-1.jpg)

The following image shows how **Team 3** sees the **Backlog**.

![Team3 PBIs](/assets/images/2013/09/team3-pbis.jpg)

### Features (High-Level Requirement of the **PBI**)

The **Features** give the ability to manage high-level requirements across two dimensions (**Teams** and **Sprints**). So the **Feature** can span multiple **Teams** and multiple **Sprints** and we will still be able to see how many **PBIs** are completed and how many remain across **Teams** and **Sprints**.

![Features-Management Team](/assets/images/2013/09/features-management-team.jpg)
