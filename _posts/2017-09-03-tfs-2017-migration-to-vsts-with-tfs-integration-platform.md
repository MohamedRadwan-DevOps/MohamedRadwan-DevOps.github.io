---
layout: post
title: "TFS 2017 Migration To VSTS with TFS Integration Platform"
date:   2017-09-03 19:11:44 +0100
---


## Introduction

Migrating [TFS](https://www.visualstudio.com/tfs/) (On-Premise) to [VSTS](https://www.visualstudio.com/team-services/) makes it a lot easier to work efficiently. There are a lot of benefits we can get, including:

- Global Availability.
- Immediate Access to updates as soon as they're available.
- Higher Security.
- Easy Deployment to Azure.

Migrating **TFS** to **VSTS** can be done using several tools, [**Microsoft Excel**](https://www.visualstudio.com/en-us/docs/work/office/bulk-add-modify-work-items-excel), [Microsoft Project](https://www.visualstudio.com/en-us/articles/adopting-vsts) or a Migration tool (which we will use). 

>Using Excel and/or Microsoft Project has limitations for images, attachments, history, and other things.
{: .prompt-warning }


I'll demonstrate another tool, which is **TFS Integration Platform**. Using TFS Integration Platform requires [**SQL Server 2012**](https://www.microsoft.com/en-us/download/details.aspx?id=29062) first, as the tool is a little bit old. This tool migrates everything except the relations between work items. Note: This tool is [**deprecated**], but you can still use it at your own risk. Migration with TFS Integration Tool is very easy, but again, we have a limitation that relations between work items can't be migrated. Before getting into the real work, you should have access to both TFS & VSTS with **full administrative privileges.** TFS Integration Platform is only helpful when you want only to migrate work items, with no need to migrate links & relations between them.

>If you would like to learn more about my personal experience of the Migration Team Foundation Server to Visual Studio Team Services using Database Import Service or TFS Migrator, have a look at [this post](https://mohamedradwan-devops.github.io/posts/migrating-team-foundation-server-to-visual-studio-team-services-using-database-import-service-tfs-migrator/).
{: .prompt-tip }


## Understanding TFS Artifacts Association and Relations

TFS doesn't only provide work items or test cases. TFS is simply everything needed to manage work. The following diagram provides some general explanation for that:

![TFS_Artifacts_And_Association](/assets/img/2017/09/TFS_Artifacts_And_Association-1024x547.png)

It's clearly shown that relations in TFS make the logic for work, therefore **it's very important to maintain the relations between work items**, not only the work items themselves.

## Step 1: Getting Environment Ready

Before getting started, we will need to install **Microsoft SQL Server 2012**. Additional help for SQL Server 2012 installation is available [here](https://technet.microsoft.com/en-us/library/bb500395%28v=sql.110%29.aspx?f=255&MSPPError=-2147217396). Please note **SQL Server 2012 is essential** for compatibility, as the **TFS Integration tool is deprecated** and is not supported for newer versions. So, make sure that you have connected to the **SQL Server 2012.** You can do this using a later version of [**SQL Server Management Studio**](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).

1. Make sure you've selected **SQL Server 2012**.
2. Click on **Connect**.

![Connecting_To_SQL_SERVER_2012](/assets/img/2017/09/Connecting_To_SQL_SERVER_2012-3-1024x552.png)

- Download & Install **Visual Studio 2010** (Required to provide Object Model for the tool) and **Visual Studio 2012** (Required to provide TFS Connectivity for the tool).

- Download & Install [TFS Integration Platform](https://marketplace.visualstudio.com/items?itemName=Willy-PSchaub.TeamFoundationServerIntegrationToolsMarch2012Relea).

>TFS Integration Platform must be installed after SQL Server 2012 and Visual Studio 2010 and Visual Studio 2012, otherwise it won't work.
{: .prompt-warning }


>If you would like to learn more about different tools and ways for Team Foundation Server to Visual Studio Team Services migration, have a look at the [quick guide about real stories for migrating Team Foundation Server to Visual Studio Team Services](https://mohamedradwan-devops.github.io/posts/published-a-quick-guide-about-real-stories-for-migrating-team-foundation-server-to-visual-studio-team-services/). The guide describes some real migration scenarios and explains how to use different tools for several cases.
{: .prompt-info }


## Step 2: Migrate

1. Open TFS Integration Platform Tool and **Click Create New**
2. Click on **Team Foundation Server Folder**
3. Choose Migration Options, you can Migrate Source Control, Work Items or Both. I choose Work Items Only.
4. Click **Open**

![TFS_Intergration_Platform_Create_New](/assets/img/2017/09/TFS_Intergration_Platform_Create_New-2-1024x499.png)

5. As a workflow type, from the drop-down menu select **One Way Migration**
6. Click on **Configure**
7. In the drop-down menu, select **TFS 11 Migration WIT Provider**

![TFS_Integration_Platform](/assets/img/2017/09/TFS_Integration_Platform-4-1024x546.png)

8. Select the right TFS Server to **connect to the original TFS**.
9. Under Team Project Collection, select the **Team Project Collection** which you want to use for this migration.
10. Under Team Projects, **navigate to the Team Project** that you will use and click on it.
11. Click on **Connect** to connect to TFS.

![TFS_Integration_Platform_Connect_To_TFS](/assets/img/2017/09/TFS_Integration_Platform_Connect_To_TFS-7-1024x546.png)

12. Click on **Configure** to configure the targeted Source and select **TFS 11 Migration WIT Provider** again.
13. Under the menu **Select the Team Foundation Server** to select the targeted **VSTS** to connect to it.
14. Under Team Project Collection, select the **Team Project Collection** which you want to use for this migration.
15. Under Team Projects, **navigate to the Team Project** that you will use and click on it.
16. Click on **Connect** to connect to VSTS.

![TFS_Integration_Connect_To_VSTS](/assets/img/2017/09/TFS_Integration_Connect_To_VSTS-6-1024x549.png)

17. Click **Save to Database**
18. Click **Start Migration**

![TFS_Integration_Start](/assets/img/2017/09/TFS_Integration_Start-7-1024x546.png)

19. Sit back and relax, **Migration can take a few hours** if you have thousands of work items. When the migration is finished, you'll see the notification in the window of the TFS Integration tool.

![TFS_Integration_Platform_Completed](/assets/img/2017/09/TFS_Integration_Platform_Completed-4-1024x548.png)

20. Additional Note, here is how your SQL Server 2012 Database looks like for Migration

![Final_Tables_Look](/assets/img/2017/09/Final_Tables_Look-1-1024x549.png)

>The post [Upgrade to TFS 2018 Has Been Done in Production](https://mohamedradwan-devops.github.io/posts/upgrade-to-tfs-2018-has-been-done-in-production/) describes a full upgrade and migration from TFS2015 to TFS2018 and describes the improvements over the old TFS 2015.
{: .prompt-tip }

## Conclusion

The **TFS Integration Platform** Tool is a pretty straightforward tool to use for migrating items from TFS to VSTS. The tool enables the migration of everything, including the acceptance criteria, discussions, history, and attachments, but not the links between the work items. However, as already mentioned at the beginning of this post, the tool is deprecated, which means that no further development will be performed and there is no current support available for it. The previous documentation for the tool is currently still available on [Codeplex](http://tfsintegration.codeplex.com/releases/view/35476). In my next post, I will describe a different tool, which can also be used for migration from TFS to VSTS. This tool, [**VSTS Sync Migrator**](http://vsts-bulk-editor.readthedocs.io/en/latest/) was developed by fellow [**MVP**](https://mvp.microsoft.com) **[Martin Hinshelwood](https://nkdagility.com/company/about-martin-hinshelwood/)**.

>You can see this video, if you would like to find more information about how to import a Git Repository
{: .prompt-tip }
{% include embed/youtube.html id='4P7QW1C4bRo' %}
