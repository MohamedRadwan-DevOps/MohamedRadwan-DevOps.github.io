---
layout: post
title: "Working with SSRS (SQL Server Reporting Server) PowerShell"
date:   2018-04-23 22:41:53 +0100
---

In this post we will see how to work with SSRS PowerShell so we can
remap SSRS or SQL Sever Reporting Server Database to an existing DB, we
will see also how to restore SSRS encryption key -�

You can see this video, if you would like
to find more information about how to restore the old database to the
new SQL server by running the command line and TFS Restore tool.
{: .prompt-tip }
{% include embed/youtube.html id='_cdH1XiBNrA' %}

- First download the PowerShell SSRS Modules using NuGet for PowerShell
(NuGet Provider), Run PowerShell as admin and type the following:

```
Install-Module -Name ReportingServicesTools
```

Because I didn\'t have NuGet for PowerShell, I got the following message

```
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program
Files\PackageManagement\ProviderAssemblies' or 'C:\Users\mradwan\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running
'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider now?
[Y] Yes [N] No [S] Suspend [?] Help (default is "Y"):
```

By agree, it will install both, NuGet and SSRS PowerShell Modules, to
displayed all the commands in that module, type -

``` 
Get-Command -Module ReportingServicesTools
```

This will display all the command 

![Module ReportingServicesTools](https://mohamedradwan-devops.github.io/wp-content/uploads/2018/04/Module-ReportingServicesTools.png)

To know how to use the needed command, type 

``` 
get-help set-rsdatabase
```

This will download the latest help and display the help, to see some
examples in how to use that command, type 

``` 
get-help set-rsdatabase -examples
```

![rsdatabase-examples](https://mohamedradwan-devops.github.io/wp-content/uploads/2018/04/rsdatabase-examples-1024x244.png)

Change the SSRS Database to map to the
old DB, I used the new name of the machine

``` 
Set-RsDatabase -DatabaseServerName MyServer_Name -Name MyReportServerDB_Name -IsExistingDatabase -DatabaseCredentialType ServiceAccount -Confirm:$false
```

Restore SSRS Encryption Key 

``` 
Restore-RSEncryptionKey -Password 'MyPassword' -KeyPath 'C:\Partial Autoamtion\CRMSRSReportKey.snk'
```


>If you would like to learn more about different tools
and ways for Team Foundation Server to Visual Studio Team Services
migration, - have a look at the [quick guide about real stories for
migrating Team Foundation Server to Visual Studio Team
Services](https://mohamedradwan-devops.github.io/posts/published-a-quick-guide-about-real-stories-for-migrating-team-foundation-server-to-visual-studio-team-services/).
The guide describes some of the real migration scenarios and explains
how to use different tools for several cases.
{: .prompt-tip}

