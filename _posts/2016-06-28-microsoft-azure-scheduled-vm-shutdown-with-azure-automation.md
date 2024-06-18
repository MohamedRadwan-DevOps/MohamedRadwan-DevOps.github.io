---
layout: post
title: "Microsoft Azure – Scheduled VM Shutdown with Azure Automation"
date: 2016-06-28 15:32:13 +0100
---

## Introduction 

Running of **Virtual Machines** depends on computing hours or in other words it depends on how many hours **Virtual Machines** are running per day. For example, if you are using **Virtual Machines** for West US region, with configuration that includes SSD drive, 2 cores, 7 GB RAM and 100 GB disk, it will cost you \$208.32 per month. **Microsoft Azure** site also provides a pricing calculator, which will show you the exact price and configuration of **Azure** features for your scenarios. Please visit <https://azure.microsoft.com/en-us/pricing/calculator/> for more details. Using **Virtual Machines** with high configuration can be very expensive, but you can reduce the cost of **Virtual Machines** by reducing its working hours with **Automated Shutdown**. This post will describe how to create an **Automated Shutdown** of **Virtual Machines** on **Windows Azure**. You will see the step-by-step instructions and a detailed walkthrough of the process of creating a **Runbook** and **Schedule** for **Virtual Machines** and how to link the **Runbook** to **Schedule** so that it gets automatically stopped at pre-defined times.

### Step 1: Create a new user in Active Directory

**PowerShell script** is Microsoft’s task-based command-line shell and scripting language designed especially for system administration. In order to run the **PowerShell Script** with **Microsoft Azure**, you will need to have a **User** linked to one of your **Directories**. If you don’t have it, you will need to create one.

1. Open the **Microsoft Azure Portal** and click on **ACTIVE DIRECTORY** from the navigation pane. **Azure Active Directory** is a comprehensive identity and access management cloud solution that provides a robust set of capabilities to manage users and groups.
2. From the list of active directories, click on our directory. In our case, it is **Default Directory**.
3. Under **default directory**, click on **USERS**.
4. From the command bar at the bottom of the Portal screen, click on **ADD USER**.

![1-1 Create a new user to run the PowerShell Script with Microsoft Azure](/assets/images/2016/06/1-1-Create-a-new-user-to-run-the-PowerShell-Script-with-Microsoft-Azure-1024x569.jpg)

>You can see [this video](https://www.youtube.com/watch?v=rgf0IgktMQU&t=2s), if you would like to find more information about the step-by-step installation and configuring process of the TFS 2017 Update 1. See which deployment type to select, deployment scenario (Basic and Advanced). How to set up the Application Tier Web Services, Search configuration settings, Reporting Services settings. Also, do not forget to install and configure the Oracle component. See the overview of Team Foundation Server Administrator Console and how to create a new Team project.

### [Continue reading here...](http://www.testhouse.net/microsoft-azure-scheduled-vm-shutdown-with-azure-automation/)
