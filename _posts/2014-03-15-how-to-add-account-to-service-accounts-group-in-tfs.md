---
layout: post
title: "How to add an account to Service Accounts Group in TFS?"
date:   2014-03-15 17:38:30 +0100
---

When I start working with [**TFS Integration Platform**](http://tfsintegration.codeplex.com/ "TFS Integration Platform"), I face the following error:

>Microsoft.TeamFoundation.Migration.Tfs2010WitAdapter.PermissionException: TFS WIT bypass-rule submission is enabled. However, the migration service account 'Radwan' is not in the Service Accounts Group on server 
at Microsoft.TeamFoundation.Migration.Tfs2010WitAdapter.TfsCore.CheckBypassRulePermission()
at Microsoft.TeamFoundation.Migration.Tfs2010WitAdapter.TfsWITMigrationProvider.InitializeTfsClient()
at Microsoft.TeamFoundation.Migration.Tfs2010WitAdapter.TfsWITMigrationProvider.InitializeClient()
at Microsoft.TeamFoundation.Migration.Toolkit.MigrationEngine.Initialize(Int32 sessionRunId)
{: .prompt-danger }

So how to add my account or the account that will be used to run 
[**TFS Integration Platform**](http://tfsintegration.codeplex.com/ "TFS Integration Platform")
for the Service Accounts Group? You can\'t add accounts using the UI so
we need to run a command line From TFS Server as the following 

```xml
C:\Program Files\Microsoft Team Foundation Server 12.0\tools> TFSSecurity.exe /g+ "Team Foundation Service Accounts" n:domain\mradwan /server:http://vsalm
```

From Visual Studio client machine Server as the following:

```xml
C:\Program Files\Microsoft Visual Studio Server 12.0\tools> TFSSecurity.exe /g+ "Team Foundation Service Accounts" n:domain\mradwan /server:http://vsalm
```

For collection, it will be as the following:

```xml
C:\Program Files\Microsoft Visual Studio Server 12.0\tools> TFSSecurity.exe /g+ "Project Collection Service Accounts" n:domain\mradwan /collection:http://vsalm:8080/tfs/Defaultcollection
```

**Note:** For sometimes you will have to type `/server:http://vsalm:8080/tfs`

![Add account Service account group](/assets/img/2014/03/add-account-service-account-group.png)

**Note**: TFS Integration Platform 2012 can work with TFS 2013 but it
needs the old object Model so just install Team Explorer 2012 or 2010
will solve the issue.

