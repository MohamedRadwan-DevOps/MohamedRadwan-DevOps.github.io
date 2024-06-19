---
layout: post
title: "PowerShell Tips"
date:   2019-01-17 04:41:44 +0100
---

In this post, I will just list some of the commands I used them during
some of my work, many of them are very easy but the idea is to list them
so I can remember what I have used :-) 

## **Prompt for input**

```powershell
$x= Read-Host -Prompt 'Please enter the value'
```

>If you would like to learn more about how to work with
SSRS PowerShell so we can remap SSRS or SQL Sever Reporting Server
Database to an existing DB, we will see also how to restore SSRS
encryption key - have a look at this post- have a look at the [**this post**](https://mohamedradwan-devops.github.io/posts/working-with-ssrs-sql-server-reporting-server-powershell/)


## **Send argument and use it with Invoke-Command**

The argument sent at the end of the script block as an array, so if I
want to access it within the script block, I just use it as \$
args\[0\], or \$args\[1\], etc.

```powershell
Invoke-Command -ComputerName "MyRemotePC" -Credential $cred -ScriptBlock {

$args[0]
$args[1]
$args[2]

} -ArgumentList $variable1,$variable2,$variable3
```

>If you would like to know more about Azure
deployments, have a look at the post [How to deploy to Azure using Team
Services Release
Management](https://mohamedradwan-devops.github.io/posts/how-to-deploy-to-azure-using-team-services-release-management/).
The post describes how Azure deployments are made easy by using Visual
Studio Team Services (VSTS) Release Management. You will see a
step-by-step tutorial on how to configure and deploy to Azure in Release
Management, and, moreover, how to configure an end-to-end pipeline for
deploying applications on Azure.
{: .prompt-info }

**Execution Policy **
[https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6) 

The Default Execution Policy is set to restricted, we can see it by typing:

```powershell
Get-ExecutionPolicy
```

We can change it and type the following to make it go to unrestricted
mode:

```powershell
Set-ExecutionPolicy unrestricted
```

## **Import Module to use its command in the current session**

```powershell
Import-Module Module Name

Examples:
---------
Import-Module WebAdministration
Import-Module AzureRM
```

AzureRM Modules has sub Modules like:

-   AzureRM.Profile
-   Azure.Storage
-   AzureRM.Automation
-   AzureRM.Backup
-   AzureRM.Billing
-   AzureRM.ContainerRegistry
-   AzureRM.DevTestLabs
-   AzureRM.KeyVault
-   And many others.

## **Get what are the current Modules loaded in the current session**

```powershell
Get-Module
```

![Get-Module PowerShell](/assets/images/2019/01/Get-Module-PowerShell.png)

```powershell
Get-Command -Module Module Name

Examples:
---------
Get-Command -Module AzureRM.Profile
```

![Get-command -Module Module Name](/assets/images/2019/01/Get-command-Module-Azure.png)

```powershell
Get-help Add-AzureRMAccount
```
![PowerShell get-help command](/assets/images/2019/01/PowerShell-get-help-command.png)

```powershell
Get-help Add-AzureRMAccount -examples
```

![PowerShell get help examples](/assets/images/2019/01/PowerShell-get-help-examples.png)

