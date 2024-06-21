---
layout: post
title: "Force Synchronizing TFS 2013 Users with Windows Accounts"
date: 2013-12-29 23:37:03 +0100
---

Sometimes we need to add users to our AD or Windows so we can add them to TFS and have them appear immediately without needing to wait for the synchronization to happen automatically. There are many ways to do that. I will explain how to do that with different methods.

**TFS Job Agent** is responsible for running this sync and other jobs. By default, this runs once an hour. We can run this job using the Web Service "JobWebService" or by using the TFS Client Object Model "Microsoft.TeamFoundation.Client". We can use the Client Object Model with a **C# Console Application** or with a **PowerShell** script.

### Use the JobWebService Directly
We need to call the **QueueJobs** web service, but unfortunately, we can't call that from the browser. We also need the **GUID** of the job. 

1. Navigate to the TFS admin Web Services.
   ![Open Webservice](/assets/img/2013/12/open-webservice.jpg)
   
2. Open the **JobService** Web Services and click on the **QueueJobs** Web Service.
   ![QueueJobs WebService](/assets/img/2013/12/queuejobs-webservice.jpg)
   
3. We can't call it from the browser and we need the **GUID** of the Job.
   ![Call QueueJobs](/assets/img/2013/12/call-queuejobs.jpg)

### Use the WebServiceStudio
We can use a very smart tool, [WebServiceStudio](http://webservicestudio.codeplex.com/), that exists on **CodePlex**. This tool enables us to call the Web Service with a GUI without writing code for the Web Service.

![QueueJobs using WebServiceStudio](/assets/img/2013/12/queuejobs-using-webservicestudio1.jpg)

### Use a PowerShell Script
We can also use the TFS Client Object Model "Microsoft.TeamFoundation.Client" with a **PowerShell** script.

![PowerShell](/assets/img/2013/12/powershell.jpg)

[Download the script](https://skydrive.live.com/redir?resid=4BCAA16D27B46600%212763) 

I made the demo on [Brian Keller VM](http://blogs.msdn.com/b/briankel/archive/2013/11/26/rtm-version-of-visual-studio-2013-alm-virtual-machine.aspx). Here are the steps you need to follow:

1. Add your user to your AD or Local accounts for the workgroup.
   ![Add Users to Windows](/assets/img/2013/12/add-users-to-windows.jpg)
   
2. Remember that we are adding the **Windows Group** to the **TFS Collection**. In our case, it's the **Administrators** group.
   ![Administrators added to the project collection](/assets/img/2013/12/administrators-added-to-the-project-collection.jpg)
   
3. Run the job using any method, and then the users will start to appear immediately.
   ![The user will appear in TFS](/assets/img/2013/12/the-user-will-appear-in-tfs.jpg)

### View Job Status
To view the status of the job, queue time, start time, or end time, run the following SQL script on the Data Tier (DT). Don't confuse the time as it is **UTC**.
```sql
USE tfs_Configuration 
SELECT TOP 100 * 
FROM [Tfs_Configuration].[dbo].[tbl_JobHistory] 
WHERE JobId='544DD581-F72A-45A9-8DE0-8CD3A5F29DFE'
```

![tbl_JobDefinition](/assets/img/2014/03/tbl_jobdefinition.png)

