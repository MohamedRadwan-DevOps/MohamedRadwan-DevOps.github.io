---
layout: post
title: "Team Foundation Server 2015 Update 3"
date: 2016-07-09 11:27:03 +0100
---

### Introduction 

From the end of June, the **Team Foundation Server 2015 Update 3** is available. **Team Foundation Server** provides a whole set of collaboration tools that can work with **Visual Studio**, **Eclipse**, **Xcode**, or your own IDE or code editor. It works with any **[Git](https://git-scm.com/)** client. It includes code repositories, continuous integration, bug and task tracking, and agile planning tools. **TFS** supports many languages such as **Java**, **Python**, **HTML5**, **JavaScript**, **C#**, and many more.

![1-Team Foundation Server 2015](/assets/img/2016/07/1-Team-Foundation-Server-2015.jpg "1-Team Foundation Server 2015")

>If you would like to know more about Azure deployments, have a look at the post [How to deploy to Azure using Team Services Release Management](https://mohamedradwan-devops.github.io/posts/how-to-deploy-to-azure-using-team-services-release-management/). The post describes how Azure deployments are made easy by using Visual Studio Team Services (VSTS) Release Management. You will see a step-by-step tutorial on how to configure and deploy to Azure in Release Management. Moreover, how to configure an end-to-end pipeline for deploying applications on Azure.

>To learn more about Agile Software Testing, have a look at the [quick guide about Agile Software Testing](https://mohamedradwan-devops.github.io/2018/01/30/published-a-quick-guide-about-agile-software-testing/). This guide presents the basic idea behind Agile methodology and its connection to software testing. It describes the structural idea of Agile and explains the importance of adaptation to changes in the fast-paced software development world.
{: .prompt-info }

### New updates 

**SSH Support for Git repos:** **TFS 2015 Update 3** enables the connection to any **Team Foundation Server Git repo** using an **SSH key**, with just the simple upload of your personal **[SSH key](https://help.github.com/articles/generating-an-ssh-key/)**. This feature is very useful especially for **Linux** or **Mac** developers.

**Dashboard Widget SDK:** With this update, you will be able to create your own **out-of-the-box [dashboard widgets](https://www.visualstudio.com/en-us/docs/integrate/extensions/develop/add-dashboard-widget)** [by using the **SDK**](https://www.visualstudio.com/en-us/docs/integrate/extensions/develop/add-dashboard-widget).

**Testing - New features:** New testing features allow the setup of test machines or premises using **SCVMM**, **VMWare**, or in the **Cloud**.

![2-Team Foundation Server 2015 Update 3](/assets/img/2016/07/2-Team-Foundation-Server-2015-Update-3.jpg "2-Team Foundation Server 2015 Update 3")

>The post [Upgrade to TFS 2018 Has Been Done in Production](https://mohamedradwan-devops.github.io/2018/01/16/upgrade-to-tfs-2018-has-been-done-in-production/) describes a full upgrade and migration from TFS2015 to TFS2018 and details the improvements over the old TFS 2015.
{: .prompt-tip }

>You can see [**this video**](https://www.youtube.com/watch?v=1A6b2Gq4j58), if you would like to find more information about how to upload an existing virtual machine to the cloud for Windows Azure. The video demonstrates how to create a Container in the Storage, how to upload a virtual hard disk to a Container, how to install and configure Azure PowerShell, how to use the command, how to connect to your Azure portal from PowerShell using a command, how to add a VHD using a command, and how long the whole process might take. The complete process of creating a VM is demonstrated including creating a disk from a VHD, choosing an Image, configuring the Virtual Machine, and installing extensions in the Virtual Machine with explanations about the possible problems during the extension installation.
{: .prompt-tip }

### Bug Fixes 

A huge number of bugs were fixed, in total around **140 bugs** from different features: **Testing**, **Agile**, **Build**, **Version Control**, **Administration**, **Extensibility**, and **Release Management**.

### Download and Update Installation 

The download is available on the **[Visual Studio main page](https://www.visualstudio.com/downloads/download-visual-studio-vs#)**. It's very important to know from which version you are upgrading. Because an upgrade to **Update 3** needs to be done from **TFS 2010 or a later release**. If you are using **TFS 2015 RTM** you can directly upgrade to **Update 3** or even from **TFS 2010 SP1** and later directly to **Update 3**. So, the upgrade is possible from a pre-release to a later build from the same release.

**Supported server operating systems:** Windows Server 2012 R2 (Essentials, Standard, Datacenter), Windows Server 2012, Windows Server 2008 R2 (minimum SP1) (Standard, Enterprise, Datacenter).

**Supported client operating systems:** Windows 10 (Home, Professional, Enterprise), Windows 8.1 (Basic, Professional, Enterprise), Windows 8, Windows 7 (minimum SP1) (Home Premium, Professional, Enterprise, Ultimate).

### Hardware requirements:

2.13 GHz or faster processor, 1 GB or greater RAM, 8 GB or more available hard disk space.

Before you start with the upgrade, it's highly recommendable to ensure that you have a complete and consistent set of database backups and to do a dry run on existing hardware in a pre-production environment. After the upgrade is done, there is a possibility that you will need to configure some of the new features. If you don't do that immediately, those features just won't be available in specific team projects until you configure them. During the upgrade, your **TFS deployment** will be offline for the duration of the upgrade. The duration depends on many factors, mostly the deployment size. For the upgrade of very large databases to **TFS 2015**, the **[TfsPreUpgrade tool](https://www.visualstudio.com/docs/setup-admin/upgrade-tfs/pre-upgrade)** is available, which will allow you to continue using **TFS** during the upgrade.

>You can see [**this video**](https://www.youtube.com/watch?v=wRG6acZX4Js), if you would like to find more information about how to stop the SharePoint services on a SharePoint machine and how to stop IIS via the Command Line (cmd). The video covers opening services using run then stopping SharePoint Administration, SharePoint Search Host Controller, SharePoint Server Search, SharePoint Timer Services, SharePoint Tracing Service, SharePoint User Code Host, SharePoint VSS Writer; then running the command line as an administrator and using the `iisreset /stop` command.

>If you are interested in developing a [Visual Studio Team Service extension](https://docs.microsoft.com/en-us/vsts/extend/overview), and you would like to know and follow the best practices for DevOps, Continuous Integration, and Continuous Delivery, have a look at the post [Develop VSTS Extension and Configure CI (Continuous Integration) and CD (Continuous Delivery Pipeline)](https://mohamedradwan-devops.github.io/posts/develop-vsts-extension-and-configure-ci-continuous-integration-and-cd-continuous-delivery-pipeline/).

### Conclusion 

**TFS** is the right choice when you need your data to stay within your network or you want access to **SharePoint** sites and reporting services that integrate with **TFS** data and tools. The newest **Update** brought some really amazing new features that will help your team be even more efficient and transparent. Even though the number of new features is not huge, they are very useful, and the number of fixed bugs for top reported issues is great.

For cases demanding high fidelity migration for work-items, the post [TFS 2017 Migration To VSTS with VSTS Sync Migrator](https://mohamedradwan-devops.github.io/posts/tfs-2017-migration-to-vsts-with-vsts-sync-migrator/) describes the migration without any limitations for migrating links, attachments, or work items.

>You can see this video, if you would like to find more information about how to create a folder for holding the backup of the database, how to open the firewall, and disable it on the current database tier.
{: .prompt-tip }

{% include embed/youtube.html id='w5QShwlyLNM' %}
