---
layout: post
title: "Working with IIS PowerShell"
date:   2018-04-23 22:51:24 +0100
---

In this post we will see how to change the credential of IIS
Application Pool using PowerShell, we will also use PowerShell to
restart the Application Pool.

>If you would like to learn more about how to work with
SSRS PowerShell so we can remap SSRS or SQL Sever Reporting Server
Database to an existing DB, we will see also how to restore SSRS
encryption key - have a look at this post- have a look at the [**this
post**](%20https://mohamedradwan.com/posts/working-with-ssrs-sql-server-reporting-server-powershell/)
{: .prompt-tip }


- First import the IIS or Web Admin module

```powershell
Import-Module WebAdministration
```

- Change the App Pool credential

```powershell
Set-ItemProperty IIS:\AppPools\CRMAppPool -name processModel -value @{userName="myDomain\myUserName";password="myPassword";identitytype=3}

Set-ItemProperty IIS:\AppPools\CrmDeploymentServiceAppPool -name processModel -value @{userName="myDomain\myUserName";password="myPassword";identitytype=3}
```

- Start the app pool after changing the credential

```powershell
Start-WebAppPool -Name "CRMAppPool"

Start-WebAppPool -Name "CrmDeploymentServiceAppPool"
```
>You can see this video*, if you would like to find more information about how to restore the old database to the
new SQL server by running the command line and TFS Restore tool.
{: .prompt-tip }
{% include embed/youtube.html id='_cdH1XiBNrA' %}

