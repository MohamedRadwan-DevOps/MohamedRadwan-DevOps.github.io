---
layout: post
title: "How Long It Will Take to Upgrade to TFS2015 with Update 1"
date: 2016-02-21 16:51:15 +0100
---

In this post, I'll be addressing the question of how long it will take to upgrade older [Team Foundation Server](https://www.visualstudio.com/en-us/products/tfs-overview-vs.aspx)versions to [TFS 2015 Update 1](https://www.visualstudio.com/en-us/news/tfs2015-update1-vs.aspx). The information on the factors that affect the **upgrade times.** For TFS 2013 Update 4 and TFS 2012 Update 4 will be presented. As well as a couple of scenarios of upgrade times. For major project changes, you can also read on how to [Upgrade TFS 2008 to TFS 2013 Update 2](https://mohamedradwan-devops.github.io/posts/upgrade-tfs-2008-to-tfs-2013-update-2-step-by-step/)or how to [Migrate a TFS Server to another Domain](https://mohamedradwan-devops.github.io/posts/migrating-tfs-server-or-collection-to-another-domain/).

### TFS requirements and compatibility 

People have asked me many questions about requirements and compatibility. Such as "Can we work with old build agent or controller?" and "Can we use VS 2008?", for example. [TFS requirements and compatibility](https://msdn.microsoft.com/en-us/library/vs/alm/tfs/administer/requirements)as well as [System Requirements](https://www.visualstudio.com/en-us/downloads/visual-studio-2015-system-requirements-vs.aspx#10)have been documented by **Microsoft**, and I encourage you to review the links for the answers to these kinds of questions.

### Collection Size based on actual data not attachment 

The time required to upgrade **TFS** depends on many things. But the prominent factors are the **version** that you're upgrading from and the **collection size**. The size of some work item attachments will not take too much time, but the collection size that really matters for builds includes work item numbers and [version control file](https://msdn.microsoft.com/en-us/library/ms181279(v=vs.90).aspx)and history; this is the main content that takes time to upgrade. If we look at the [changes](https://www.visualstudio.com/en-us/news/tfs2015-vs.aspx)from TFS 2013 to TFS 2015, we will find there are [huge changes in the DB schema](https://www.visualstudio.com/en-us/news/tfs2015-vs.aspx#schema)- this was done to support the renaming for team projects. Also, as long as the collection DB size increases with project content, it will take more time. For more details on **versioning assembly** with TFS, you can read [this article](https://mohamedradwan-devops.github.io/posts/versioning-assembly-during-tfs-build-2013/).

### TFS Pre-Upgrade Tool 

Tools such as [TfsPreUpgrade](https://www.visualstudio.com/docs/setup-admin/upgrade-tfs/pre-upgrade)can also be used to help reduce the upgrade time, but this only works for **TFS deployments** meeting certain requirements. For the TfsPreUpgrade tool to be applicable, the **deployment** needs to be on TFS2013 Update 4 or Update 5 and have its associated collection databases on an [Enterprise edition of SQL Server](https://www.microsoft.com/en-us/cloud-platform/sql-server-editions-enterprise)or on [SQL Server 2012](https://msdn.microsoft.com/en-us/library/bb500435(v=sql.110).aspx)SP1+ or [SQL Server 2014](https://msdn.microsoft.com/library/bb500435(v=sql.120).aspx)CU3+.

### TFS2013.4 to TFS2015.1 

The following is example for upgrading to TFS 2015 with Update 1 from [TFS 2013 with Update 4](https://support.microsoft.com/en-us/kb/2994375); the collection size was 360GB and the log file was 40GB. It took just under 11 hours to complete.
[![TFS2015 update1](/assets/img/2016/02/tfs2015-update1.png)](/assets/img/2016/02/tfs2015-update1.png)

### TFS2012.4 to TFS2015.1

The following is example for upgrading to TFS 2015 with Update 1 from [TFS 2012 with Update 4](https://support.microsoft.com/en-us/kb/2872520); the collection size was 40GB and the log file was 5GB. It took just over 14 minutes to complete.
[![TFS2012 to TFS2015](/assets/img/2016/02/tfs2012-to-tfs2015.jpg)](/assets/img/2016/02/tfs2012-to-tfs2015.jpg)

>You can see [this video](https://www.youtube.com/watch?v=7C6LG6k4wcU&t=4s), if you would like to find more information about my personal experience of the migration Team Foundation Server to Visual Studio Team Services using Database Import Service or TFS Migrator tool provided by Visual Studio Team. Going through all six phases of the migration, following the migration guide provided by Microsoft as a walkthrough. You will see how to get started with the migration process and which prerequisites should be completed.

The most important prerequisite is that you must have Azure Active Directory in order to use TFS Migrator tool. See more about the two different process models supported by VSTS, Inherited and Hosted XML. See which decisions you should make and how to validate them. For example, which customizations you should keep and which one to remove. To prepare the first collection dacpac, first you should prepare Azure Storage Container, create dacpac file and afterwards upload it. To prepare the second collection Azure VM. You should install SQL Server, backup the DB from the collection and upload it to the Azure storage container. See first how to import (dry - run) and how to change the configuration afterwards in order to import (production).
