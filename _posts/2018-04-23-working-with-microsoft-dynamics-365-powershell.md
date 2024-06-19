---
layout: post
title: "Working with Microsoft Dynamics 365 PowerShell"
date: 2018-04-23 23:05:41 +0100
---

In this post, we will see how to use **PowerShell to change some values for Microsoft Dynamics 365**.

First, add the PowerShell snap-in for the CRM module:
[https://msdn.microsoft.com/en-us/library/gg197664(v=crm.6).aspx](https://msdn.microsoft.com/en-us/library/gg197664(v=crm.6).aspx)



```powershell
Add-PSSnapin Microsoft.Crm.PowerShell
```

>If you would like to learn more about how to work with SSRS PowerShell so we can remap SSRS or SQL Server Reporting Server Database to an existing DB, and also how to restore SSRS encryption key, have a look at the [**this post**](https://mohamedradwan-devops.github.io/posts/working-with-ssrs-sql-server-reporting-server-powershell/).
{: .prompt-info}

---

Get the current CRM Server information:
[https://docs.microsoft.com/en-us/powershell/module/microsoft.crm.powershell/get-crmserver?view=dynamics365ce-ps](https://docs.microsoft.com/en-us/powershell/module/microsoft.crm.powershell/get-crmserver?view=dynamics365ce-ps)

```powershell
Get-CrmServer
```

The information of the current CRM Server will be displayed. 

![Get-CrmServer info](/assets/images/2018/04/Get-CrmServer-info-1024x123.png)


By default, this will connect to the current CRM server URL. So it looks at the address in the Deployment manager address for (Deployment Web Service) as shown in the image below (Dynamics 365 Deployment Manager). If you want to pass the CRM address, you need to provide it as a parameter (**-DwsServerUrl**) for that command.

```powershell
Get-CrmServer -DwsServerUrl "http://localhost" -Credential "mradwan"
```

Remember, because I use **-DwsServerUrl**, I have to provide the credential parameter as well. If I put only the username, it will prompt for the password:

![Get-CrmServer-DwsServerUrl-Credential](/assets/images/2018/04/Get-CrmServer-DwsServerUrl-Credential-1024x416.png)

Get-CrmServer-DwsServerUrl-Credential

![Get-CrmServer -DwsServerUrl -Credential prompt for password](/assets/images/2018/04/Get-CrmServer-DwsServerUrl-Credential-prompt-for-password-1024x194.png)

Get-CrmServer -DwsServerUrl -Credential prompt for password

If you want to send the credential without prompting for the password, you need to declare a variable to hold the credential object and use a secure string:

```powershell
$username = 'localdomain\mradwan'
$password = ConvertTo-SecureString "mypassword" -AsPlainText -Force
$cred = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $username, $password


```powershell
$username = 'localdomain\mradwan'
$password = ConvertTo-SecureString "my password" -AsPlainText -Force
$cred = new-object -typename System.Management.Automation.PSCredential -ArgumentList $username, $password
```

Now call the same command but instead of send the user name for
credential parameter to send the credential object

```powershell
Get-CrmServer -DwsServerUrl "http://localhost" -Credential $cred
```

![Get-CrmServer -DwsServerUrl -Credential with credential object](/assets/images/2018/04/Get-CrmServer-DwsServerUrl-Credential-with-credential-object-1024x268.png)

This is how it looks like when I display what is inside the credential object:

![PowerShell Credential object values](/assets/images/2018/04/PowerShell-Credential-object-values.png)

- We can also Disable or Enable CRM Organization


```powershell
Disable-CrmOrganization "OrgnizationName"

Enable-CrmOrganization "OrgnizationName"
```

>You can see this videoif you would like to find more information about an introduction and overview of a series of videos about Microsoft Dynamics development. This includes an overview of the Microsoft Dynamics CRM itself, installing Microsoft Dynamics 2016 on Azure VM and how to upgrade to Dynamics 365, how to develop Dynamics CRM plugins, how to debug Microsoft Dynamics CRM projects, create and run unit tests using FakeXRMEasy and Microsoft Fakes, JavaScript and front-end unit tests as well as code quality using JSHint, and how to create and run UI tests. It also covers how to integrate all the practices as part of CI/CD (Continuous Integration and Continuous Delivery).
{: .prompt-tip }
{% include embed/youtube.html id='rEJMBwuKY6Y' %}

- Get the current CRM Server settings [here](https://technet.microsoft.com/en-us/library/dn833084.aspx)


```powershell
Get-CrmSetting
```

It will ask me which settings I want.


![Get-CrmSetting](/assets/images/2018/04/Get-CrmSetting.png)

If I pass "WebAddressSettings", it will show me all the addresses in the Deployment Manager address.

![WebAddressSettings](/assets/images/2018/04/WebAddressSettings.png)

> **Tip**: If you would like to learn more about how to create a new Dynamics 365 CRM environment locally with Windows Server 2016 Standard Edition, then prepare this machine to be ready to upload to the cloud (Azure), upload the machine to Azure, and create an image of that machine. After that, we will start using this image for creating a new virtual machine with Dynamics 365 and reconfigure the machine to fix all the problems caused by changing the hard disk and the machine name, which will cause problems for SSRS (SQL Server Reporting Server). All IIS application pools crashed, the SQL Server name crashed, and of course, Dynamics 365 CRM doesn't work. I will show exactly how to solve all those problems so we can have a new copy of an existing Dynamics CRM machine and make it work fine. Have a look at [**this post**](https://mohamedradwan-devops.github.io/posts/automatically-creating-staging-environment-for-dynamics-365-on-the-cloud/).

Remember, if I don't provide an address to any of those PowerShell commands, it will use the one in the Deployment Manager address for (Deployment Web Service).

![Dynamics 365 Deployment Manager](/assets/images/2018/04/Dynamics-365-Deployment-Manager.png)

> **More Info**: If, after adding a new user to [Dynamics 365](https://dynamics.microsoft.com/en-gb/), you get the following error: *You do not have permissions to see this view. Contact a system administrator crm*, have a look at [**this post**](https://mohamedradwan-devops.github.io/posts7/fix-you-do-not-have-permissions-to-see-this-view-contact-a-system-administrator-crm/).

## Import CRM organization

[https://technet.microsoft.com/en-us/library/dn833059](https://technet.microsoft.com/en-us/library/dn833059) we can use  Import-CrmOrganization to import
a Microsoft Dynamics 365 organization database into the deployment.

```powershell
$OrganisationName = "TestOrg"
$DatabaseName = "$($OrganisationName)_MSCRM"
$SrsUrl = "http://$env:computername/ReportServer
$SqlServerName = $env:computername
$DwsServerUrl = "http://$env:computername.ad.devopsvisions.com"
$UserMappingMethod1 = "ByAccount"
$UserMappingMethod2 ="ByMappingXmlFile"
```

So we can see that we have different ways ! For user mapping which map
the users in the imported organization to the users in the current
deployment. ByAccount, which means the same accounts on both directions

```powershell
Import-CrmOrganization -SqlServerName $SqlServerName -DatabaseName $DatabaseName -SrsUrl $SrsUrl -DisplayName 
$DisplayName -Name $Name -UserMappingMethod $UserMappingMethod -Credential $cred -DwsServerUrl $DwsServerUrl
```

-� ByMappingXmlFile. which means we will have XML file that mapp each
account to another account and domain to other domain if needed.

```powershell
Import-CrmOrganization -SqlServerName $SqlServerName -DatabaseName $DatabaseName -SrsUrl $SrsUrl 
-DisplayName $DisplayName -Name $Name -UserMappingMethod $UserMappingMethod -UserMappingXmlFile $pathToFile -Credential $cred -DwsServerUrl $DwsServerUrl
```


![Import CRM Organization from Deployment Manager](/assets/images/2018/04/Import-CRM-Organization-from-Deployment-Manager-1024x465.png)

![Generate a new mapping file when Import CRM Organization from Deployment Manager](/assets/images/2018/04/Generate-a-new-mapping-file-when-Import-CRM-Organization-from-Deployment-Manager-1024x430.png)


