---
layout: post
title: "What's New in TFS 2012?- Project Management Tool"
date:   2012-05-30 20:37:58 +0100
---

In this series I will start introducing what's new in Visual Studio 11
and Team Foundation Server 11 (TFS 11) or as we expect to be [Visual Studio 2012](http://www.microsoft.com/visualstudio/11/en-us "Visual Studio 2012") and [Team
Foundation Server
2012](http://msdn.microsoft.com/en-us/library/fda2bad5%28v=vs.110%29 "Application Lifecycle Management with Visual Studio and Team Foundation Server") (TFS
2012)

1.  [Introduction](https://mohamedradwan-devops.github.io/posts/whats-new-in-tfs-11-introduction/ "Introduction")
2.  [Project Management Tool](https://mohamedradwan-devops.github.io/posts/whats-new-in-tfs-2012-management-tool/ "TFS Management Tool")
3.  [SSDT (SQL Server Developer Tool)](https://mohamedradwan-devops.github.io/2012/08/02/whats-new-in-tfs-2012-ssdt-sql-server-developer-tool/ "SSDT (SQL Server Developer Tool)")
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


## Project Management Tool

In this post I will talk about the following improvement in the Project
Management tools for TFS 11 (Team Foundation Server )

1.  ### Teams

2.  ### Team Web Access For Agile Management

-   ### Teams

### What is team feature?

[![What is team](/assets/images/2012/05/What-is-team.jpg)](/assets/images/2012/05/What-is-team.jpg)


The team feature is the third dimension of the [team
project](http://msdn.microsoft.com/en-us/magazine/gg983486.aspx "Visual Studio TFS Team Project and Collection Guidance").

1.  [Iteration](http://msdn.microsoft.com/en-us/library/hh500418(v=vs.110)#AddIterations "Add or Modify Team Iterations ")
    (Time Dimension)
2.  [Areas](http://msdn.microsoft.com/en-us/library/hh500418(v=vs.110)#AddArea "Add or Modify Team Areas ")
    (Features or Module Dimension)
3.  [Teams](http://msdn.microsoft.com/en-us/library/hh528603(v=vs.110) "Understanding Teams")
    (People Dimension)

Just think of a large project that has many teams, for example **Team1**
and **Team2**. **Team1** has 2 weeks sprints but **Team2** has 4 weeks
sprints, each team has different day-off, different sprint delivery and
daily stand up meeting and many others, remember that they share the
same product backlog. So by introduced team feature, we can manage this
different very easy, **Wow it's really awesome!** So each team can
have separate and different:

1.  Team members
2.  Team favorite
3.  Backlog
4.  Burndown chart
5.  Sprints
6.  Days-off
7.  etc.


If we don't segment our team project into teams, all team capabilities
are available for the team project, which acts as the default team. To
understand team feature more, assume that there is nothing called team
project any more, it's just a team now and if you don't create any so
you are working on the default team (Which will be the team project) so
the team project has at least one team by default and this is what we
will work on. 

[![Manage Teams](/assets/images/2012/05/Manage-Teams.png)](/assets/images/2012/05/Manage-Teams.png)

[![](https://public.sn2.livefilestore.com/y1poiVWIGXUukUqkzdeCJY4cHvSqN1_6z-mJc8_4KHHVjHCjtdPp6spPSJMHAWhSlkE5o9-DY1dGz234pM34ruTBw/Manage%20Teams.png?psid=1 "TFS Team Settings")](https://public.sn2.livefilestore.com/y1poiVWIGXUukUqkzdeCJY4cHvSqN1_6z-mJc8_4KHHVjHCjtdPp6spPSJMHAWhSlkE5o9-DY1dGz234pM34ruTBw/Manage%20Teams.png?psid=1)

Team feature supports small teams that work on different product areas
to manage their backlog and iteration, separate from other teams. We
define and manage team membership through Team Web Access. We manage
team members through the Administration mode in Team Web Access.

**For detailed explanation see the following video** 

{% include embed/youtube.html id='cJUh3fKSVTU' %}


Links: [What's New in the Visual Studio Team Foundation Server](http://blogs.msdn.com/b/visualstudioalm/archive/2011/09/20/visual-studio-team-foundation-server-11-developer-preview-what-s-new-for-team-foundation-server.aspx?ocid=soc-n-eg-elite--MRadwan "What's new in Team Foundation Server")
[Understand Teams](http://msdn.microsoft.com/en-us/library/hh528603%28v=vs.110%29.aspx "Understand Team")

-   ### Team Web Access for Agile Management

There are a lot of improvements introduced in TFS 11 in Team Web Access,
and I believe it has become a first class citizen, at least for me! There
is a big improvement in performance and usability, to minimize the number
of round-trips to the server, to make a richer UI experience. There are a
lot of small features but the most important new features are Backlog
and Board pages. I will also explain the Home Page.

1.  ### Backlog

2.  ### Board

3.  ### Home Page



-   ### Backlog

We have many internal features in the Backlog like:



1.  Drag and Drop to prioritize the PBI (Product Backlog Item) and
    assign them to sprints
2.  Sprints divided into **Past**, **Current** and **Future** based on
    start and end date of the iteration and the current date.
3.  Quick add **PBI** or **Bugs** to the Backlog
4.  Real time velocity chart
5.  Real time Burndown chart
6.  Forecast where to assign our **PBIs** based on the estimated
    velocity





[![](https://public.sn2.livefilestore.com/y1pKtlmmzarr39duGbhB7u2z54F9LXXIH1_Bwz3dzNcWU0C_cQ4g5JxNfdFMz9vymxgYVav1Q8nyYTGhBUOuZ8egw/Backlog1.png?psid=1 "Backlog 1"){.alignnone
width="1364"
height="514"}](https://public.sn2.livefilestore.com/y1pKtlmmzarr39duGbhB7u2z54F9LXXIH1_Bwz3dzNcWU0C_cQ4g5JxNfdFMz9vymxgYVav1Q8nyYTGhBUOuZ8egw/Backlog1.png?psid=1)



[![](https://public.sn2.livefilestore.com/y1pUi6WwmHQ7yJ_Jeye5A38bsaoSsnDGg2HCGdLj7E_eQ6HTDpVo2aHdTu1lcCiIUhCOkYkHr-rH28I-Wiamr-z6g/Backlog2.png?psid=1 "Backlog 2"){.alignnone
width="1363"
height="542"}](https://public.sn2.livefilestore.com/y1pUi6WwmHQ7yJ_Jeye5A38bsaoSsnDGg2HCGdLj7E_eQ6HTDpVo2aHdTu1lcCiIUhCOkYkHr-rH28I-Wiamr-z6g/Backlog2.png?psid=1)

[![](https://public.sn2.livefilestore.com/y1pJapIsEjRGu7LRzbfTBnqVLnKPRCo7iK853NDipT7SfiVaCFTCOPzQjN9AMpOp2y2CA8e94f7PBJ8tzsWIjDCrg/Backlog3.png?psid=1 "Backlog 3"){.alignnone
width="1364"
height="515"}](https://public.sn2.livefilestore.com/y1pJapIsEjRGu7LRzbfTBnqVLnKPRCo7iK853NDipT7SfiVaCFTCOPzQjN9AMpOp2y2CA8e94f7PBJ8tzsWIjDCrg/Backlog3.png?psid=1)

The Backlog page will enable us to manage our backlog of the whole
product or the team project (Default Team) or any team inside the team
project. Remember only the selected iterations (Sprints if we use Scrum
process template) what will appear in the backlog page divided into 3
sections Past, Current and Future, this divide based on the iteration
start and end date and current date. Remember also to use Backlog feature
we have to select at least one iteration and one area. 

**Note:** To customize the Backlog page or days-off of team capacity we will need to
customize the process template.

-   ### Board

It's the Agile digital wall, it supports drag and drop and view from
different dimensions like PBI/Bugs and team members, it also supports
member filter. First we have to notice that it's a task board for PBI or
Bugs, so we must have PBI and Tasks for this sprint.


[![](https://public.sn2.livefilestore.com/y1pVCDvXX6NQv2Wz4OUYrn1ItbrRJDjttM1zqqClAWTgjk912qmUo6DVJ329kR0U28GCEOOzmB4BYqWMDgzoCsYzA/TaskBoard.png?psid=1 "Task Board Team Web Access TFS"){.alignnone
width="1362"
height="622"}](https://public.sn2.livefilestore.com/y1pVCDvXX6NQv2Wz4OUYrn1ItbrRJDjttM1zqqClAWTgjk912qmUo6DVJ329kR0U28GCEOOzmB4BYqWMDgzoCsYzA/TaskBoard.png?psid=1)

The parent level of the task (PBI or Bugs in Scrum) will appear as
vertical data and all child task appear horizontal data beside it PBI or
Bug. It will appear in 3 states: To Do, In Progress and Done (Scrum
template). [Note: To make auto self-assigned for task, you have to choose
your name from the person at the top right corner in the Board
page.]
-   ### Home Page

The home page mainly represents a way of shortcut of most activities
we perform, so let's see them from a high level view:

1.  Create work items shortcuts
2.  Work load vs. capacity of current Sprint (real time)
3.  Burndown of current Sprint (real time)
4.  Team Favorites (queries, build definitions, source control and
    branches)
5.  Activities (shortcuts for several activities)
6.  Members (shortcut to view and manage members)
7.  Administration (shortcut to manage Iterations and Areas)
8.  Recent project and teams (move from team to team)
9.  Search work items ([Note: use double quotation around your
    criteria])
10. Profile (email, picture)
11. Settings (iterations, areas, security, alerts, members) by default
    for current team

See the following image to identify each feature with its number.


[![](https://public.sn2.livefilestore.com/y1pQDGQDhHgjeR8g7dH8hsZI9I9y5wPWmd-_k6aifFdnfOFav-eJqWhvR6lEdIG4y4MutbrJVlDhuSvidxRKhhHAA/TFS%20Team%20Web%20Access%20Home%20Page.png?psid=1 "TFS Team Web Access Home page"){.alignnone
width="1361"
height="686"}](https://public.sn2.livefilestore.com/y1pQDGQDhHgjeR8g7dH8hsZI9I9y5wPWmd-_k6aifFdnfOFav-eJqWhvR6lEdIG4y4MutbrJVlDhuSvidxRKhhHAA/TFS%20Team%20Web%20Access%20Home%20Page.png?psid=1)

**For detailed explanation see the following videos**

**Part 1**

{% include embed/youtube.html id='BRGTtCOKAwk' %}

**Part 2**

{% include embed/youtube.html id='vMhQtw2K3do' %}

**Part 3** 

{% include embed/youtube.html id='IFlyqmk5cVQ' %}

Links: [What's New in the Visual Studio Team Foundation Server](http://blogs.msdn.com/b/visualstudioalm/archive/2011/09/20/visual-studio-team-foundation-server-11-developer-preview-what-s-new-for-team-foundation-server.aspx?ocid=soc-n-eg-elite--MRadwan "What's new in Team Foundation Server")
[Working with Tam Web Access](http://msdn.microsoft.com/en-us/library/ee523998%28v=vs.110%29 "Working with Team Web Access")
[Agile Planing and Iterations](http://msdn.microsoft.com/en-us/library/hh500404%28v=vs.110%29 "Agile Planning and Iterations")
[What's new in Planning and Tracking](http://msdn.microsoft.com/en-us/library/hh913786%28v=vs.110%29#overview "What's New in Planning and Tracking")
