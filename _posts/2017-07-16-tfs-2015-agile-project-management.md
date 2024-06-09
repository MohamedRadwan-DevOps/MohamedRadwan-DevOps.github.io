---
layout: post
title: "TFS 2015 Agile Project Management"
date:   2017-07-16 20:15:22 +0100
---

### Introduction

The new **Agile Project Management** features in **TFS 2015** provides
better support for aligning across teams while giving the individual
teams the autonomy and the flexibility they need to operate as the ones.
Many improvements have been made to the boards in **TFS 2015**. Each
individual feature team can choose how they want to work. An
organization can build a road map and settle progress of feature teams
towards that road map while allowing the teams flexibility. You can also
visit **Visual Studio website** and learn more about **TFS
2015**:*[Kanban Basics](https://www.visualstudio.com/en-us/docs/work/kanban/kanban-basics)**, **[Customize an Agile
Tool](https://www.visualstudio.com/en-us/docs/work/customize/customize-agile-tools)** and many more.

>The post [Upgrade to TFS 2018 Has Been Done in
Production](https://mohamedradwan.com/posts/upgrade-to-tfs-2018-has-been-done-in-production/)
describes a full upgrade and migration from TFS2015 to TFS2018 and
describes the improvements over the old TFS 2015.
{: .prompt-tip }


### Part 1: Board Improvements

1.  1.  There is an **Add Button** on **Feature Team Board**. You can
        now add items to the board easily without opening the new work
        item form. Click on **Add Button**.
    2.  The new item is added to the board now. By default, it adds the
        item on top of the backlog, but if you don\'t like that position
        you don\'t have to go back to the backlog anymore. You can
        reorder the items on the board itself.


![add-button TFS](/assets/images/2016/09/Add-Button.jpg "add-button TFS")

3. If you made a typo, you
can change the title without opening the boards by clicking on **Pen
Icon**. 

![changing-title TFS](/assets/images/2016/09/Changing-title.jpg "changing-title TFS")

4. In previous versions of
TFS you could add bugs to the boards but that would affect all teams
within the team projects because teams were definitely an organization.
**TFS 2015** now gives each team the choice how they want to treat bugs.
This team is using only the **Kanban board** and as such wants to see
bugs on their board. Go to **Settings**, go to **bugs section** and
choose **bugs appear on the backlog**. 

![bugs-on-backlog TFS](/assets/images/2016/09/Bugs-on-backlog.jpg "bugs-on-backlog TFS") 

5. The bugs now appear on the
board. 6. You are probably familiar with the ability to add new columns
to the boards. This team wants to change their columns to design,
implementation, code review and acceptance tests which was already
possible in **TFS 2013**. 

![new-board-configuration-options TFS](/assets/images/2016/09/New-board-configuration-options.jpg "new-board-configuration-options TFS")

7. All active columns are
visible in the top bar of the **Kanban** board and the new columns are
now added to the board.

>You can see this video if you would like to find more information about a walkthrough introducing the Release Management and Build Automation using TFS
2017/2015. Step by step about all process, starting from creating the
project, check in the code in the source control, create a build
definition and trigger the build, and also create a release pipeline.
Learn how to configure properly the build steps, including Copy Files
and Publish Build Artifacts. See how to create new release definition,
add environments and link to build definition. Afterwards see how to add
tasks to the release definition, like Windows Machine File Copy and
configure it properly.
{: .prompt-tip }

{% include embed/youtube.html id='vev3Czaa1pA' %}


![columns-added-to-board TFS](/assets/images/2016/09/columns-added-to-board.jpg "columns-added-to-board TFS")

8. Using a pool model is
typical for **Kanban** where team members put items into the next
column. To support that model **TFS 2015** have introduced **split
column**. So lets split the code review column. Click on the **gear
icon** on the top right hand corner. 9. Click on **Columns.**

![split-columns TFS](/assets/images/2016/09/split-columns.jpg "split-columns TFS")

10. Click the **check box**.

11. Click on **OK**.

![split-code-review TFS](/assets/images/2016/09/split-code-review.jpg "split-code-review TFS")

12. You will now see two
sections: a **doing section** and a **done section**. 

![code-review-splitted TFS 2015](/assets/images/2016/09/Code-review-splitted-1.jpg "code-review-splitted TFS 2015")

13. The board now also
supports an **expedite swimlane**. This gives the team the ability to
identify the items that needs to be finished as soon as possible. Click
on the **gear icon**. 14. Click on **Swimlanes.** 

![swimlanes TFS](/assets/images/2016/09/swimlanes.jpg "swimlanes TFS")

15. Click on **Add Swimlane
button**. 16. Click on **OK** on the bottom right hand corner.

![expedite-swimlane TFS](/assets/images/2016/09/expedite-swimlane.jpg "expedite-swimlane TFS")

17. The **Expedite swimlane** is now added to the board.

![expedite-swimlane-added-to-board](/assets/images/2016/09/expedite-swimlane-added-to-board.jpg "expedite-swimlane-added-to-board")

[More Info]{.ion-info}In some of the previous posts you can find
high-level descriptions of
[Agile](https://mohamedradwan.com/2017/07/08/quick-intro-to-agile/)
principles and the usage of some [Agile
tools](https://mohamedradwan.com/2017/07/16/tfs-2015-agile-project-management/)
and [Agile methodology](http://agilemanifesto.org/).
{: .prompt-tip }


### Part 2: Build and Track Roadmap

**TFS 2015** also provides a great overview across teams inside the
organization. This team tracks the **epics**. When the team walks up to
the backlog they can drill down into the details of the **epic** to see
the progress of the teams in the organization all the way to **tasks**.

>You can see this videoIf you would like to find more information about my personal experience
of the migration Team Foundation Server to Visual Studio Team Services
using Database Import Service or TFS Migrator tool provided by Visual
Studio Team. Going through all six phases of the migration, following
the migration guide provided by Microsoft as a walk through. You will
see how to get started with the migration process and which
prerequisites should be completed. The most important prerequisite is
that you must have Azure Active Directory in order to use TFS Migrator
tool.
{: .prompt-tip }
{% include embed/youtube.html id='7C6LG6k4wcU' %}

See more about the two different process models supported by VSTS,
Inherited and Hosted XML. See which decisions you should make and how to
validate them, for example which customizations you should keep and
which one to remove. To prepare the first collection dacpac, first you
should prepare Azure Storage Container, create dacpac file and
afterwards upload it. To prepare the second collection Azure VM, you
should install SQL Server, backup the DB from the collection and upload
it to the Azure storage container. See first how to import (dry - run)
and how to change the configuration afterwards in order to import
(production).

![Team Epic TFS 2015](/assets/images/2016/09/Team-epics.jpg "Team Epic TFS 2015")

And if you are inside a **feature team** you can do the same drill down from the **features**
into **stories** into **tasks**.

![Features TFS 2015](/assets/images/2016/09/Features.jpg "Features TFS 2015")

>The post [Upgrade to TFS 2018 Has Been Done in
Production](https://mohamedradwan.com/posts/upgrade-to-tfs-2018-has-been-done-in-production/)
describes a full upgrade and migration from TFS2015 to TFS2018 and
describes the improvements over the old TFS 2015.
{: .prompot-tip }

### Conclusion

You can download the latest version of **TFS** from the **[Visual Studio
download page](https://beta.visualstudio.com/downloads/)**. Learn more about the latest updates
available from these resources:

-   **[What\'s new in Visual Studio
    2015](https://msdn.microsoft.com/library/bb386063%28v=vs.140%29.aspx)** 
    
    - to review the latest features of the **Visual Studio** client [Visual Studio Team
    Services](https://www.visualstudio.com/en-us/docs/overview) to get started using our cloud
    offering, **Visual Studio Team Services** which provides end-to-end
    support for software development without the overhead of maintaining
    and managing servers.
-   **[Visual Studio download
    page](https://beta.visualstudio.com/downloads/)** - to download the latest version of
    **TFS**

