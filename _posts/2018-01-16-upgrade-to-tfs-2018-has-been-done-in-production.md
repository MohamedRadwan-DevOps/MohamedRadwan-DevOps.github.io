---
layout: post
title: "Upgrade to TFS 2018 Has Been Done in Production"
date: 2018-01-16 01:14:52 +0100
---

During the previous week, I was at a customer site for migrating their **[TFS](https://www.visualstudio.com/tfs/) 2015** to **[VSTS](https://www.visualstudio.com/team-services/)**. The customer required a full fidelity migration. Therefore **TFS 2015 update 3** was upgraded to **TFS 2018**. I am currently still onsite to continue the full migration; I will later share how to use the **TFS Migrator tool** by **Microsoft** or the [Database Import Tooling](https://www.visualstudio.com/team-services/migrate-tfs-vsts/).

[Tip]{.ion-tip} If you would like to learn more about my personal experience of the Migration Team Foundation Server to Visual Studio Team Services using Database Import Service or TFS Migrator, the TFS Database Import Service, also known shorthand as the Import Service, provides a high fidelity way to migrate collection databases from TFS to VSTS. Have a look at [**this post**](https://mohamedradwan.com/posts/migrating-team-foundation-server-to-visual-studio-team-services-using-database-import-service-tfs-migrator/).

The upgrade described in this post was smooth and included a few improvements over the old **TFS 2017**. Only these improvements will be discussed below. If anyone would like to follow the complete step-by-step upgrade process, have a look at my guide for [Upgrading-TFS-2010-to-TFS-2012-with-Migration-to-a-New-Hardware-Guide](https://github.com/DevOpsFounder/Upgrading-TFS-2010-to-TFS-2012-with-Migration-to-a-New-Hardware-Guide) describing all the steps. The present post only includes the new features for the upgrade process, which were not discussed previously. The steps taken during the upgrade process are presented below.

1. **Team Foundation Server 2018: Configuration Wizard**. Here we are using the normal Server Configuration, as usual.

   ![1-Team Foundation Sever 2018 Configuration Wizard Start](/assets/images/2018/01/1-Team-Foundation-Sever-2018-Configuration-Wizard-Start-1024x698.png)

2. **Team Foundation Server 2018: Prepare Configuration and Configure IIS and other components**. Also here the usual process procedures were followed.

   ![2-Team Foundation Sever 2018 Configuration Prepare Configuration and Configure IIS](/assets/images/2018/01/2-Team-Foundation-Sever-2018-Configuration-Prepare-Configuration-and-Configure-IIS-1024x699.png)

3. **Team Foundation Server 2018 Configuration: Pre-Production Upgrade Testing**. This was a new and, in my opinion, a very important feature in the upgrade. Since we keep the old name of the server after the upgrade, we have to change this name immediately in case of a dry run or a trial migration.

   ![3- Team Foundation Sever 2018 Configuration Pre-Production Upgrade Testing](/assets/images/2018/01/3-Team-Foundation-Sever-2018-Configuration-Pre-Production-Upgrade-Testing-1024x698.png)

4. **Team Foundation Server 2018 Configuration: Automatic remapping of database connection string**. The image below shows that database connection strings are remapped automatically. TFS collections and server identifiers are changed automatically as well. And even scheduled jobs are automatically stopped. This is very convenient, as you don't have to do it manually. And, therefore, you don't have to be concerned about any conflicts.

   ![4- Team Foundation Sever 2018 Automatic remapping of database connection string](/assets/images/2018/01/4-Team-Foundation-Sever-2018-Automatic-remapping-of-database-connection-string-1024x700.png)

5. **Provide Service Account for Team Foundation Server 2018**. We are now back to the usual steps.

   ![5- Provide Service Account for Team Foundation Sever 2018](/assets/images/2018/01/5-Provide-Service-Account-for-Team-Foundation-Sever-2018-1024x701.png)

6. **Team Foundation Server 2018 Configuration: Configuration in progress**.

   ![6-Team Foundation Sever 2018 Configuration Configuration in progress](/assets/images/2018/01/6-Team-Foundation-Sever-2018-Configuration-Configuration-in-progress-1024x702.png)

7. **Team Foundation Server 2018: Collection Configuration**.

   ![7- Team Foundation Sever 2018 Collection Configuration](/assets/images/2018/01/7-Team-Foundation-Sever-2018-Collection-Configuration-1024x705.png)

8. **Team Foundation Server 2018: Configuration and Upgrade Completed**.

   ![8- Team Foundation Sever 2018 Configuration Completed](/assets/images/2018/01/8-Team-Foundation-Sever-2018-Configuration-Completed-1024x705.png)

>You can see this video, if you would like to find more information about the step-by-step installation and configuration process of the TFS 2017 Update 1. See which deployment type to select, deployment scenario (Basic and Advanced), how to set up the Application Tier Web Services, Search configuration settings, and Reporting Services settings. Also, do not forget to install and configure the Oracle component. See the overview of Team Foundation Server Administrator Console and how to create a new Team project.
{: .prompt-tip }
{% include embed/youtube.html id='rgf0IgktMQU' %}

>If you would like to learn more about different tools and ways for Team Foundation Server to Visual Studio Team Services migration, have a look at the [quick guide about real stories for migrating Team Foundation Server to Visual Studio Team Services](https://mohamedradwan.com/posts/published-a-quick-guide-about-real-stories-for-migrating-team-foundation-server-to-visual-studio-team-services/). The guide describes some of the real migration scenarios and explains how to use different tools for several cases.
{: .prompt-info }
