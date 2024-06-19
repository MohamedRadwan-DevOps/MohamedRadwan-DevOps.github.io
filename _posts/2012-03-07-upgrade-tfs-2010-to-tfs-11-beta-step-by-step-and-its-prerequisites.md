---
layout: post
title: "Upgrade TFS 2010 to TFS 11 Beta Step by Step and Its Prerequisites"
date:   2012-03-07 16:54:55 +0100
---

[Updated on March 13, 2012]

[Before upgrade, you must see the following video.++]
[Upgrading-to-Team-Foundation-Server-11-Core-Server](http://channel9.msdn.com/Blogs/VisualStudio/Upgrading-to-Team-Foundation-Server-11-Core-Server-Upgrade#c634668199383903825)

>Upgrading from TFS 11 Developer Preview to TFS 11 Beta is not supported.
{: .prompt-info}

When I tried to upgrade my existing environment of TFS 2010 to TFS 11 Beta, first I saw the video for [NORTHWEST CADENCE](http://blog.nwcadence.com/upgrading-to-team-foundation-server-11-tfs-11-beta/ "NORTHWEST CADENCE") by Steven Borg. Thanks, Steven! However, when I tried to upgrade my environment, I faced the first issue which is described [here](https://mohamedradwan.com/posts/upgrade-tfs-11-beta-failure-and-its-solution/ "TFS 11 Upgrade issue"). Then, I had another configuration failure because I had to update SQL Server 2008 R2 SP1 to its Cumulative Update 1. The error was as follows:

> [The SQL instance used does not meet the minimum requirements for TFS. You must update SQL Server 2008 R2 to the latest Service Pack and Cumulative Update. Minimum requirements are SP1, Cumulative Update 1]

You can find SQL 2008 R2 SP1 [here](http://www.microsoft.com/download/en/details.aspx?id=26727 "SQL 2008 R2 SP1").  
You can find the Cumulative update [here](http://support.microsoft.com/kb/2544793 "Cumulative update").

>The hardware requirements for SharePoint now require 8 GB of RAM, and if we use a single machine (TFS + SharePoint + DB), it's recommended to have at least 10 GB of RAM.
{: .prompt-info}

### Step by Step

Let's see the upgrade process step by step:

![3-6-2012 3-07-18 PM](/assets/images/2012/03/3-6-2012-3-07-18-PM.png)

![3-6-2012 3-32-33 PM](/assets/images/2012/03/3-6-2012-3-32-33-PM.png)

![3-6-2012 3-33-28 PM](/assets/images/2012/03/3-6-2012-3-33-28-PM.png)

![3-6-2012 3-34-07 PM](/assets/images/2012/03/3-6-2012-3-34-07-PM.png)

![3-6-2012 5-02-43 PM](/assets/images/2012/03/3-6-2012-5-02-43-PM.png)

![3-6-2012 5-03-16 PM](/assets/images/2012/03/3-6-2012-5-03-16-PM.png)

![3-6-2012 5-04-32 PM](/assets/images/2012/03/3-6-2012-5-04-32-PM.png)

![3-6-2012 5-05-17 PM](/assets/images/2012/03/3-6-2012-5-05-17-PM.png)

![3-6-2012 5-07-08 PM](/assets/images/2012/03/3-6-2012-5-07-08-PM.png)

![3-7-2012 6-40-31 PM](/assets/images/2012/03/3-7-2012-6-40-31-PM.png)

[And now OceanSoft upgraded to TFS 11 Core component](https://mohamedradwan.com/posts/now-oceansoft-upgraded-to-tfs-11-beta-with-go-live-support/ "OceanSoft upgrade to TFS 11 Beta")
