---
layout: post
title: "How to solve some Dynamics CRM deployment and permissions errors"
date:   2018-05-14 20:45:21 +0100
---

>If you face any of the following problems, While installing **Dynamics CRM** getting error at "System Checks" regarding permission for DB Window Active Directory issue during CRM installation Unable to create CRM Organization using PowerShell. Unable to Import CRM Organization Permissions error while using Import-CrmOrganization to import a Dynamics CRM Organization SysAdminCheck raising error: You do not have sufficient permission to perform this operation on the specified organization database The current user does not have required permissions (read/write) for the following Active Directory group: CN=ReportingGroup Permission error on the report server folders
{: .prompt-danger }


>If you would like to learn more about how to work with SSRS PowerShell so we can remap SSRS or SQL Server Reporting Server Database to an existing DB, also how to restore SSRS encryption key - have a look at [**this post**](https://mohamedradwan-devops.github.io/posts/working-with-ssrs-sql-server-reporting-server-powershell/)
{: .prompt-info }


>For more information about how to work with Kubernetes cluster and deploy it to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see **[Kubernetes cluster for beginner](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/)**
{: .prompt-tip }
{% include embed/youtube.html id='4DUhc0MjdUc' %}

## Solution:

Make sure that CRM service accounts and user accounts have the right permission for Active Directory, local machine, SSRS security, SQL Server security.

**For Active Directory:** Make sure that needed accounts (user and service) are part of the following groups and provide Full Control permission for the needed accounts to:

- Full Control on the Reporting Group
- All [administration]{.gt-baf-back} on the PrivReporting Group
- Total Control to the SQLAccess Group
- Perfect Control on the PrivUser Group

![Active Directory CRM Reporting Group and permissions](/assets/img/2018/05/Active-Directory-CRM-Reporting-Group-and-permissions-1024x727.png)

>For more information about how to work with **Docker** like, pull docker image, run docker image and work with container, see **[Docker for beginners](https://mohamedradwan-devops.github.io/posts/docker-for-beginners-step-by-step-tutorial/)**
{: .prompt-info }
{% include embed/youtube.html id='3RJv6yVfaRE' %}


![Active Directory CRM Reporting Group and permissions added to SQL](/assets/img/2018/05/Active-Directory-CRM-Reporting-Group-and-permissions-added-to-SQL.png)

**For local admin:** Adding your needed accounts (user and service) to local admin if possible will solve many issues for SSRS permission otherwise add them to SSRS.

**For SSRS:** Add needed accounts (user and service) under the Site Settings and under the Home Folder settings security.

**For SQL Server:** Make sure that needed accounts (user and service) have sysadmin or create DB permission.

#### **Notes:**

The most important user account is the account you used to log in and manage Dynamics deployment. The most important service account is the service account used for **CrmDeploymentServiceAppPool**.

>If you would like to learn more about how to create a new Dynamics 365 CRM environment locally with Windows Server 2016 Standard Edition, then prepare this machine to be ready to upload to the cloud (Azure), then upload the machine to Azure, then create an image of that machine. After that, we will start using this image for creating a new virtual machine with Dynamics 365 then reconfigure the machine to fix all the problems because changing the hard disk and the machine name which will make problems for SSRS (SQL Server Reporting Server), all IIS application pools crashed, the SQL Server name crashed, and of course Dynamics 365 CRM doesn\'t work, so I will show exactly how to solve all those problems so we can have a new copy of an existing Dynamics CRM machine and make it work fine - have a look at [**this post**](https://mohamedradwan-devops.github.io/posts/automatically-creating-staging-environment-for-dynamics-365-on-the-cloud/)
{: .prompt-tip }

>For more information about how to work with **Git** with animation. All commands will be represented in graphical animation. E.g. git branch, git merge, git rebase, git cherry-pick and many others, see **[Mastering Git with animation](https://mohamedradwan-devops.github.io/posts/mastering-git-from-beginner-to-advanced-step-by-step-with-graphical-animation-commands/)**
{: .prompt-tip }
{% include embed/youtube.html id='ZgCCnv9LxzA' %}


**Links:**
[https://msdn.microsoft.com/en-us/library/gg197630(v=crm.6).aspx](https://msdn.microsoft.com/en-us/library/gg197630(v=crm.6).aspx)
[https://social.microsoft.com/Forums/en-US/104f390a-7aff-454f-b82c-44af307a74ae/the-current-user-does-not-have-required-permissions-readwrite-for-the-following-active-directory?forum=crm](https://social.microsoft.com/Forums/en-US/104f390a-7aff-454f-b82c-44af307a74ae/the-current-user-does-not-have-required-permissions-readwrite-for-the-following-active-directory?forum=crm)

>If, after adding a new user to [Dynamics 365](https://dynamics.microsoft.com/en-gb/), you get the following error: *You do not have permissions to see this view. Contact a system administrator crm,* - have a look at [**this post**](https://mohamedradwan-devops.github.io/posts/fix-you-do-not-have-permissions-to-see-this-view-contact-a-system-administrator-crm/)
{: .prompt-tip }