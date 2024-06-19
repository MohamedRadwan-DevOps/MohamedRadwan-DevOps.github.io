---
layout: post
title: "What's New in TFS 2012?- SSDT (SQL Server Developer Tool)"
date:   2012-08-02 07:38:05 +0100
---

In this series, I will start introducing what's new in Visual Studio 11 and Team Foundation Server 11 (TFS 11) or as we expect to be [Visual Studio 2012](http://www.microsoft.com/visualstudio/11/en-us "Visual Studio 2012") and [Team Foundation Server 2012](http://msdn.microsoft.com/en-us/library/fda2bad5%28v=vs.110%29 "Application Lifecycle Management with Visual Studio and Team Foundation Server") (TFS 2012).

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

## SSDT (SQL Server Developer Tool)

In this post, I will talk about the new tool for **Database Development** in [Visual Studio 2012](http://www.microsoft.com/visualstudio/11/en-us "Visual Studio 2012"), which was previously known as Database Professional or Visual Studio Database Project. Now we have a new tool that is very similar to the old one but with a lot of enhancements and new features. For more info about the comparison between SQL Server Developer Tool and Visual Studio 2010 Database Projects, see the following link: [SSDT vs. VS2010 Database Projects](http://blogs.msdn.com/b/ssdt/archive/2011/11/21/sql-server-data-tools-ctp4-vs-vs2010-database-projects.aspx?ocid=soc-n-eg-elite--MRadwan "SQL Server Developer Tool vs. VS2010 Database Projects"). For more info about SQL Server Developer Tool, see the following link: [SQL Server Data Tools Team Blog](http://blogs.msdn.com/b/ssdt/?ocid=soc-n-eg-elite--MRadwan "Official team blog for SSDT, a tool for on and off-premise database development").

#### The following is a step-by-step video that covers the entire topic.

{% include embed/youtube.html id='tNjp2hwuXkg' %}

### SQL Express LocalDB

I will start by **SQL Express LocalDB** because it is part of **SSDT** now. It will make sense if we get a clear explanation about that point before we talk about **SSDT**.

There is a new version of SQL Express called **SQL Express LocalDB**. [Microsoft SQL Server 2012 Express LocalDB](http://msdn.microsoft.com/en-us/library/hh510202.aspx) is an execution mode of SQL Server Express. It is not a service anymore...

**LocalDB** is specially created for developers to provide the SQL Server Database Engine needed to develop, debug, and run database development, so the **Developer Tools** provide us as developers a way to write and test T-SQL code without having to manage a full server instance of SQL Server as before.

[Download Microsoft SQL Server 2012 Express](http://www.microsoft.com/en-us/download/details.aspx?id=29062)

[Introducing LocalDB, and improved SQL Express with helpful Q&A](http://blogs.msdn.com/b/sqlexpress/archive/2011/07/12/introducing-localdb-a-better-sql-express.aspx?ocid=soc-n-eg-elite--MRadwan)

Connect to SQL Express LocalDB using SQL Server Management Studio 2008 R2.

![Connect to SQL Express LocalDB](/assets/images/2012/08/connect-to-sql-express-localdb.jpg)

Examine how SQL Express LocalDB runs as a process with the same credentials that open the application (SQL Management Studio in our case).

![SQL Express LocalDB runs as a process](/assets/images/2012/08/sql-express-localdb-run-as-a-process.jpg)

Connect to SQL Express LocalDB using Visual Studio SQL Server Object Explorer.

![Connect to SQL Express LocalDB using SQL Server Object Explorer](/assets/images/2012/08/connect-to-sql-express-localdb-using-sql-server-object-explorer.jpg)

Examine how SQL Express LocalDB runs as a process with the same credentials that open Visual Studio.

![SQL Express LocalDB runs as a process with SQL Server Explorer](/assets/images/2012/08/sql-express-localdb-run-as-a-process-with-sql-server-explorer.jpg)

### SSDT (SQL Server Developer Tool)

As mentioned before, this is the new tool that replaced **Visual Studio Database Project**. I will describe the following capabilities:

- **Table and Stored Procedure Designer**
- **Debugging SQL Project using SQL Express LocalDB**
- **Publishing Database locally and on Build Server**
- **SQLCMD variables**

For more info, see the [SQL Server Data Tools Team Blog](http://blogs.msdn.com/b/ssdt/?ocid=soc-n-eg-elite--MRadwan "Official team blog for SSDT, a tool for on and off-premise database development").

#### Table and Stored Procedure Designer

Now there is a very powerful designer for Tables and Stored procedures. It looks similar to the HTML designer in Visual Studio that splits the page into two sections, one for the designer and the second for the code, and they are synchronized with each other.

![SSDT designer and editor](/assets/images/2012/08/ssdt-designer-and-editor.jpg)

#### Debugging SQL Project using SQL Express LocalDB

We can run any Stored procedure without connecting to a real Database. This is using the Debug Configuration of SQL Server Database Project and the SQL Express LocalDB feature.

First, we will create a new SQL Server Database Project.

![SQL Database Project](/assets/images/2012/08/sql-database-project.jpg)

Configure the debug option to use SQL Express LocalDB (configured by default).

![SSDT and SQL Server Project Debug](/assets/images/2012/08/ssdt-and-sql-server-project-debug.jpg)

Examine the database files that will be attached to the process of SQL Express LocalDB so we can execute our T-SQL commands without needing to maintain a SQL Server instance.

![SQL Server Project Database file](/assets/images/2012/08/sql-server-project-database-file.jpg)

Examine the SQL Database Project after we execute some Stored Procedures by adding a database connection.

![Open the Database file of the SQL Server Database Project](/assets/images/2012/08/open-the-database-file-of-the-sql-server-database-project.jpg)

#### Publishing Database locally and on Build Server

The **Publish** feature is the same as the **Deploy** feature in the **Visual Studio Database Project** but with a lot of enhancements that really make life very easy.

Right-click on **Database 1** > **Publish** > **Edit**, this will enable you to enter the **Target Connection String**.

![Publish SQL Server Database Project](/assets/images/2012/08/publish-sql-server-database-project.jpg)

You may click **Advanced** to configure the advanced options of the deployment.

![Advanced settings in the Publish Database](/assets/images/2012/08/advanced-settings-in-the-publish-database.jpg)

After we set our connection string and advanced options, click on **Publish** and examine how the database is published to your database server.

![Publish Database and examine that it exists](/assets/images/2012/08/publish-database-and-examine-that-its-exist.jpg)

We can have multiple publishing profiles so we can publish our Database Project differently on different machines.

![Multi Publishing Profile](/assets/images/2012/08/multi-publishing-profile1.png)

After creating the build definition, we will put the needed publish profile in the MS Build Argument. This is the profile that will be used while the build machine builds the project.

`"/t:Build /t:Publish /p:SQLPublishProfilePath=profilename.xml"`

![Build definition to use Publish profile](/assets/images/2012/08/build-definition-to-use-publish-profile.jpg)

After we queue a build using our build definition that specifies the needed publish profile, the database will be published using the specified publish profile.

![Build Success and Publish the Database to the SQL Server](/assets/images/2012/08/build-success-and-publish-the-database-to-the-sql-server.jpg)

#### SQLCMD variables

This feature enables us to use any variable during our build or publish and gives the needed value at the appropriate time.

I just add a variable (**x**) so I can give it a value during the publish or during the build, but remember if the value will need to be assigned during the build on the build server, the value must be saved inside the publish profile.

I can also give the variable (**x**) a default value.

![SQLCMD Variables](/assets/images/2012/08/sqlcmd-variables.jpg)

When I click publish on the SQL Database Project, the publish requests me to provide a value for this variable (**x**).

![SQLCMD Variables with Publish window of the SQL Server Database Project](/assets/images/2012/08/sqlcmd-variables-with-publish-window-of-the-sql-server-database-project.jpg)

Links: 
- [Intro about SQL Server Development Tools](http://msdn.microsoft.com/en-us/magazine/hh394146.aspx)
- [Microsoft SQL Server Data Tools: Database Development from Zero to Sixty in Build Event 2012](http://channel9.msdn.com/Events/TechEd/Europe/2012/DBI311 "Microsoft SQL Server Data Tools: Database Development from Zero to Sixty Build 2012 Event")
- [SQL Server Data Tools Team Blog](http://blogs.msdn.com/b/ssdt/?ocid=soc-n-eg-elite--MRadwan "Official team blog for SSDT, a tool for on and off-premise database development")
- [SSDT vs. VS2010 Database Projects](http://blogs.msdn.com/b/ssdt/archive/2011/11/21/sql-server-data-tools-ctp4-vs-vs2010-database-projects.aspx?ocid=soc-n-eg-elite--MRadwan "SQL Server Developer Tool vs. VS2010 Database Projects")
- [Microsoft SQL Server Data Tools By MVP Isablle](http://channel9.msdn.com/posts/Microsoft-SQL-Server-Data-Tools "Microsoft SQL Server Data Tools By MVP Isablle")
- [A First Look at SQL Server Data Tools](http://channel9.msdn.com/posts/SQL11UPD00-REC-02 "A First Look at SQL Server Data Tools")
- [Download Microsoft SQL Server 2012 Express](http://www.microsoft.com/en-us/download/details.aspx?id=29062)
- [Introducing LocalDB, and improved SQL Express with helpful Q&A](http://blogs.msdn.com/b/sqlexpress/archive/2011/07/12/introducing-localdb-a-better-sql-express.aspx?ocid=soc-n-eg-elite--MRadwan)
