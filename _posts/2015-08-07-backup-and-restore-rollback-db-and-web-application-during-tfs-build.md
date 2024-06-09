---
layout: post
title: "Backup and Restore (Rollback) DB and Web Application during TFS Build"
date: 2015-08-07 13:23:16 +0100
---

One of our TFS assignments needed to extend the current build and deployment process which includes [Creating and Deploying Web package](https://mohamedradwan.com/posts/creating-and-deploying-web-package-during-tfs-build-2013/), [Deploying Database](https://mohamedradwan.com/posts/deploying-ssdt-during-local-and-server-build/), [Versioning Assembly](https://mohamedradwan.com/posts/versioning-assembly-during-tfs-build-2013/), running post-integration tests after deployment, etc., to include rollback which will perform backup and restore. We agreed on performing the backup during the deployment and the restore will be a separate build definition. For the backup during the deployment, I added the following section that backs up the DB and the Web App.

![Backup DB and Web Sequence](/assets/images/2015/08/backup-db-and-web-squence1.png)

>You can see [this video](https://www.youtube.com/watch?v=_cdH1XiBNrA) if you would like to find more information about how to restore the old database to the new SQL server by running the command line and TFS Restore tool.
{: .prompt-tip }

{% include embed/youtube.html id='_cdH1XiBNrA' %}


```powershell
"-verb:sync -source:iisapp='" + IISApplicationPath + "',computerName='" + ServerIP + "',userName='" + IISUserName + "',password='" + IISPassword + "', -dest:package='" + BuildDetail.BuildDefinition.Name + "_Backup.zip',encryptPassword=password123"
```

The build definition for that part will be as the following: 

[![Backup DB and Web Squence-parameters](/assets/images/2015/08/backup-db-and-web-squence-parameters.png)](/assets/images/2015/08/backup-db-and-web-squence-parameters.png)

>If you would like to know more about the best practices for [DevOps](https://www.visualstudio.com/team-services/devops/), Continuous Integration and Continuous Delivery, you can have a look at the following post: [Configure CI (Continuous Integration) and CD (Continuous Delivery Pipeline)](https://mohamedradwan.com/posts/develop-vsts-extension-and-configure-ci-continuous-integration-and-cd-continuous-delivery-pipeline/).
{: .prompt-tip }

For the rollback and restore, I added the following section that restores the backup for both DB and Web. For the DB, I had to get exclusive access so I can restore the DB even if there are active connections from other clients.

![Restore DB and Web Sequence](/assets/images/2015/08/restore-db-and-web-squence1.png)

```powershell
"cmd.exe /k Sqlcmd -Q \"\"use master alter database " + DBNameForBackup + " set single_user with rollback immediate RESTORE DATABASE " + DBNameForBackup + " FROM DISK='" + DBNameForBackup + "_Bakup.bak' WITH REPLACE alter database " + DBNameForBackup + " set multi_user\"\" -S " + DBServerOrIP
```

```powershell
"-verb:sync -source:package=\"C:\\Windows\\SysWOW64\\" + BuildDefinitionDeploymentName + "_Backup.zip\" -dest:iisapp='" + IISApplicationPath + "',computerName='" + ServerIP + "',userName='" + IISUserName + "',password='" + IISPassword + "',-setParam:kind=ProviderPath,scope=iisApp,value='" + IISApplicationPath + "'"

```

> You can see **[this video](https://www.youtube.com/watch?v=YXOr7OoLNUU) if you would like to find more information about how to open the SQL Server Reporting Services Configuration Manager on the new Data Base tier (which is the application tier) and change the Database to the restored Data Base, how to restore the SSRS Encryption Key, how to solve the issue with the Deployment pointing on two servers using the RSKeyMngmt and RSKeyMngmt - r commands in the Command Prompt.

- The build definition for that part will be as the following:

[![Restore DB and Web Squence-parameters](/assets/images/2015/08/restore-db-and-web-squence-parameters.png)](/assets/images/2015/08/restore-db-and-web-squence-parameters.png)

## Some good commands that I end up with:

### PowerShell 

Backup a SQL Database using PowerShell
```powershell
Backup-SqlDatabase -ServerInstance . -Database database1 -BackupAction Database
```
```powershell
Backup-SqlDatabase -ServerInstance 10.43.94.222 -Database database1 -BackupAction Database
```
Backup a SQL Database using Invoke-Sqlcmd

```powershell
Invoke-Sqlcmd -Query "BACKUP DATABASE DATABASE1 TO DISK='Backups\\MyDB.bak'" -ServerInstance 10.43.94.222 -Username YourUserName -Password YourPassword
```
Restore a SQL Database using Invoke-Sqlcmd

```powershell
Invoke-Sqlcmd -Query "RESTORE DATABASE DATABASE1 FROM DISK='Backups\\MyDB.bak' WITH REPLACE" -ServerInstance 10.43.94.222 -Username YourUserName -Password YourPassword
```

Set Database to Single User Mode and back to Multi User Mode
```powershell
Invoke-Sqlcmd -Query "use master; alter database database1 set single_user with rollback immediate; alter database database1 set multi_user" -ServerInstance 10.43.94.222 -Username YourUserName -Password YourPassword
```
Restore a SQL Database and set to Multi User Mode in a single command

```powershell
Invoke-Sqlcmd -Query "use master; alter database database1 set single_user with rollback immediate; RESTORE DATABASE DATABASE1 FROM DISK='Backups\\MyDB.bak' WITH REPLACE; alter database database1 set multi_user" -ServerInstance 10.43.94.222 -Username YourUserName -Password YourPassword

```

>If you would like to learn more about using the
[Build Variables](https://docs.microsoft.com/en-us/vsts/build-release/concepts/definitions/build/variables?tabs=batch)
in [VSTS](https://www.visualstudio.com/team-services/) and Release
Management, - have a look at the following post: [VSTS Build variables and Echo](https://mohamedradwan.com/posts/vsts-build-variables-and-echo/).
The post describes how to see the output at any point of time, while
automating a process, through setting variables and displaying them
during the build.
{: .prompt-info }



### sqlcmd

```bash
# Backup a SQL Database
sqlcmd -U YourUserName -P YourPassword -S 10.43.94.222 -Q "BACKUP DATABASE DATABASE1 TO DISK='Backups\\MyDB.bak'"
```

```bash
# Set Database to Single User Mode, Restore, and Set to Multi User Mode
sqlcmd -U YourUserName -P YourPassword -S 10.43.94.222 -Q "use master; alter database database1 set single_user with rollback immediate; RESTORE DATABASE DATABASE1 FROM DISK='Backups\\MyDB.bak' WITH REPLACE; alter database database1 set multi_user"

```

## Delete DB Backup T-SQL 

```sql
EXECUTE master.dbo.xp_delete_file 0, N'G:\Microsoft SQL Server\MSSQL11.BGAPIDB01Q\MSSQL\Backup', N'BAK'
```

### Invoke Process by call .bat file 

```powershell
& (BuildDirectory + "src\Scripts\BackDB_Test.bat")
```

### Invoke Process by cmd.exe and arguments

```powershell
"cmd.exe"
```
```powershell
"cmd.exe /k Sqlcmd -Q \"BACKUP DATABASE DATABASE1 TO DISK='Backups\\MyDB.bak'\" -S 10.43.94.189 -U YourUserName -P YourPassword"

```

>You can see this video If you would like to find more information about how to use the cliconfig command in the Command Prompt in the elevated mode to enable the TCP/IP and create a new alias in the SQL Server Client Network Utility, how to use the get-spdatabase in the SharePoint Management
Shell and how to map each database with the correct ID using the db-ChangeDatabaseInstance method.
{: .prompt-tip }

{% include embed/youtube.html id='dtcdfilQar8' %}


### Web 
#### MSDeploy Commands

- Sync IIS Application to a Local Package

```bash
msdeploy -verb:sync -source:iisapp='Default web site/Lara' -dest:package='defaultWebsiteBackup.zip',encryptPassword=password123
```
- Sync IIS Application to a Remote Package

```bash
msdeploy -verb:sync -source:iisapp='Default web site/Lara' -dest:package='defaultWebsiteBackup.zip',encryptPassword=password123 -computerName=172.18.0.333 -userName=YourUserName -password=YourPassword
```
- Sync Local Package to IIS Application

```bash
msdeploy -verb:sync -source:package="C:\Program Files (x86)\IIS\Microsoft Web Deploy V3\defaultWebsiteBackup.zip" -dest:auto -setParam:kind=ProviderPath,scope=iisApp,value='Default web site/Lara'
```

- Sync Local Package to Remote IIS Application

```bash
msdeploy -verb:sync -source:package="C:\Windows\SysWOW64\defaultWebsiteBackup.zip" -dest:iisapp='Default web site/Lara' -computerName=172.18.0.333 -userName=YourUserName -password=YourPassword -setParam:kind=ProviderPath,scope=iisApp,value='Default web site/Lara'
```

>Read about basic guidelines that you need to consider
when building a **product backlog** in the following post, [Requirements
(Epic, Feature, User Story), Task Size and Estimation in Agile and
Scrum](https://mohamedradwan.com/posts/requirements-epic-feature-user-story-task-size-and-estimation-in-agile-and-scrum/),
and also about its maintaining and refinement of product backlog in [Key
tips for Maintaining good product backlog in Agile and
Scrum](https://mohamedradwan.com/posts/key-tips-for-maintaining-good-product-backlog-in-agile-and-scrum/).
{: .prompt-tip }

