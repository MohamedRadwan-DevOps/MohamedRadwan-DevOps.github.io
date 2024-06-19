---
layout: post
title: "Monitoring TFS 2012 using SCOM (System Center Operation Manager 2012)"
date: 2012-12-30 09:14:36 +0100
---

Besides using SCOM (System Center Operation Manager) in ALM to eliminate the boundaries between development and operations in the DevOps approach, we can also use it to monitor the TFS Server itself. [TFS 2012 (Team Foundation Server 2012) Monitoring Management Pack available](http://www.microsoft.com/en-us/download/details.aspx?id=35773 "TFS 2012 (Team Foundation Server 2012) Monitoring Management Pack "){target="_blank"} now, it will help us monitor Microsoft Team Foundation Server 2012. It monitors different TFS components like application tier server instances, team project collections, build servers, and proxy servers. 

The list of objects that can be monitored:

- TeamFoundationServer2012.TFSInstallation
- TeamFoundationServer2012.TFSApplicationTier
- TeamFoundationServer2012.TFSAdministrationWebService
- TeamFoundationServer2012.TFSAuthorizationWebService
- TeamFoundationServer2012.TFSBuildWebService
- TeamFoundationServer2012.TFSProjectCollection
- TeamFoundationServer2012.TFSRegistrationWebService
- TeamFoundationServer2012.TFSVersionControlWebService
- TeamFoundationServer2012.TFSWarehouse
- TeamFoundationServer2012.TFSWebAccess
- TeamFoundationServer2012.TFSWorkItemTrackingWebService
- TeamFoundationServer2012.TFSBuildAgent
- TeamFoundationServer2012.TFSBuildController
- TeamFoundationServer2012.TFSBuildServer
- TeamFoundationServer2012.TFSProxy

Health Explorer is used to show the Health Model, as we can see it showing the state of the object and various monitors of that item arranged in a tree view.

![Health Explorer for SCOM TFS Management Pack](/assets/images/2012/12/health-explorer-for-scom-tfs-management-pack-1.png)
Health Explorer can also show unhealthy states ([red]{style="color:#ff0000;"}). We can know the possible causes and resolutions from the list in the "Knowledge" article on the right.

![Health Explorer has error for SCOM TFS Management Pack](/assets/images/2012/12/health-explorer-has-error-for-scom-tfs-management-pack.jpg)

Some existing alerts

![Alerts](/assets/images/2012/12/alerts-1.jpg)
