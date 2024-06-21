---
layout: post
title: "Dynamics 365 CRM Tools and Process tips"
date:   2018-07-18 21:52:02 +0100
---

### Introduction:

When we start thinking about **SDLC** (Software Development Life Cycle) and [**DevOps**](https://blogs.msdn.microsoft.com/devops/) for Microsoft Dynamics 365 CRM, we must highlight very important tools and processes. In this post I am going to explain 3 tools that come with Microsoft Dynamics SDK (Software Development Kit). These tools are:

1. SolutionPackager.exe
2. Configuration Migration (DataMigrationUtility.exe)
3. PackageDeployer.exe

>If you would like to learn more about how to work with SSRS PowerShell so we can remap SSRS or SQL Sever Reporting Server Database to an existing DB, we will see also how to restore SSRS encryption key - have a look at [**this post**](https://mohamedradwan-devops.github.io/posts/working-with-ssrs-sql-server-reporting-server-powershell/)
{: .prompt-tip }

## 1. SolutionPackager.exe

It\'s a tool that can reversibly decompose a Microsoft Dynamics 365 compressed solution file into multiple XML files and other files so that these files can be easily managed by a source control system. When we export CRM solution from CRM, it\'s compressed into a few files but with large content for each file. The main reason for exporting the CRM solution is to import it to another CRM org or instance, so there is no need to have well-structured files. But when we talk about understanding the change and working as a team, we would like to keep that under source control. So, it\'s better if we structure those files well into many files which will be easy and manageable to see the changes by others in each file. Each file may represent an item so we can track changes. See the following images:

![CRM SolutionPackager](/assets/img/2018/07/CRM-SolutionPackager-1024x478.png)

![CRM SolutionPackager workflow](/assets/img/2018/07/CRM-SolutionPackager-workflow-1024x634.png)

<https://msdn.microsoft.com/en-gb/library/jj602987.aspx>
<https://msdn.microsoft.com/en-gb/library/jj602974.aspx>

>If you would like to learn more about how to change the credential of IIS Application Pool using PowerShell, we will also use PowerShell to restart the Application Pool - have a look at [**this post**](https://mohamedradwan-devops.github.io/posts/working-with-iis-powershell/)
{: .prompt-info }

>If you would like to learn more about how to use PowerShell to change some values for Microsoft Dynamics 365 - have a look at [**this post**](https://mohamedradwan-devops.github.io/posts/working-with-microsoft-dynamics-365-powershell/)
{: .prompt-tip }

## 2. Configuration Migration (DataMigrationUtility.exe)

It\'s a tool that moves configuration data across Microsoft Dynamics 365 instances and organizations. Configuration data is different from end-user data (account, contacts, and so on). While this tool is used for moving configuration data, it also moves user data as well, so you can think of the data as mixed between configuration data and user data. It also uses the GUID of the data which is very important to keep GUIDs the same across multiple CRM instances. This is a very important point, if you have, for example, a workflow that references some data, behind the scenes, it uses the GUID of that data and if we have the same data in 2 different CRM instances they will not work as the GUID is not the same. See the following images:

![CRM Configuration Migration](/assets/img/2018/07/CRM-Configuration-Migration-1024x562.png)

![CRM Configuration Migration workflow](/assets/img/2018/07/CRM-Configuration-Migration-workflow-1024x716.png)

![CRM Configuration Migration process and files](/assets/img/2018/07/CRM-Configuration-Migration-process-and-files.png)

<https://technet.microsoft.com/library/dn647421.aspx>

There is also another community tool which copies user data with their GUIDs (e.g. opportunities) over multiple instances.
<https://technet.microsoft.com/library/dn647421.aspx>
<https://github.com/lucasalexander/AlexanderDevelopment.ConfigDataMover>

>If, after adding a new user to [Dynamics 365](https://dynamics.microsoft.com/en-gb/), you get the following error: *You do not have permissions to see this view. Contact a system administrator crm,* - have a look at [**this post**](https://mohamedradwan-devops.github.io/posts/fix-you-do-not-have-permissions-to-see-this-view-contact-a-system-administrator-crm/)
{: .prompt-info }

## 3. PackageDeployer.exe

It\'s a tool to deploy packages on Microsoft Dynamics 365. A package can consist of:

- One or more Dynamics 365 solution files.
- Flat files (CSV) or exported configuration data files from the Configuration Migration tool
- Custom code that can run before, while, or after the package is deployed
- HTML that can display at the beginning and end of the deployment process

See the following images:

![CRM Package Deployer](/assets/img/2018/07/CRM-Package-Deployer-1024x529.png)

![CRM Package Deployer workflow](/assets/img/2018/07/CRM-Package-Deployer-workflow-1024x550.png)
<https://msdn.microsoft.com/en-gb/library/dn688182.aspx>
<https://technet.microsoft.com/en-us/library/dn647420.aspx>

>If you would like to learn more about Microsoft Dynamics development, including the overview of the Microsoft Dynamics CRM itself, installing Microsoft Dynamics 2016 on Azure VM and how to upgrade to Dynamics 365, how to develop Dynamics CRM plugin, how to debug Microsoft Dynamics CRM project, create and run unit tests using FakeXRMEasy and Microsoft Fakes, JavaScript and front end unit tests as well as code quality using JSHint, also how to create and run UI and how to integrate all the practices as part of the CI/CD (Continuous Integration and Continuous Delivery), - have a look at [**this post**](https://mohamedradwan-devops.github.io/posts/devops-for-microsoft-dynamics/)
{: .prompt-tip }
