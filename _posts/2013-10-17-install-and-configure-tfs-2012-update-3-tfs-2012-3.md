---
layout: post
title: "Install and configure TFS 2012 Update 3 (TFS 2012.3)"
date: 2013-10-17 22:14:02 +0100
---

In this post, I will explain a step-by-step installation and configuration for TFS 2012 Update 3 (TFS 2012.3)

- [Download the TFS with Update 3](http://www.microsoft.com/en-us/download/details.aspx?id=38185 "Visual Studio Team Foundation Server 2012 with Update 3")
- [Download Agents for Visual Studio 2012 Update 3](http://www.microsoft.com/en-us/download/details.aspx?id=38186 "Agents for Visual Studio 2012 Update 3")
- [Download Visual Studio 2012 Update 3](http://www.microsoft.com/en-us/download/details.aspx?id=39305 "Visual Studio 2012 Update 3")
- [More info about Update 3](http://support.microsoft.com/kb/2835600 "Description of Visual Studio 2012 Update 3")

Insert the **VS2012.3 TFS Server ENU** media in your machine and click on **tfs_server.exe**. Notice that you can’t change the path since it detects the previous installation (TFS 2012.2).

![Visual Studio TFS 2012 Update 3 -1](/assets/images/2013/10/visual-studio-tfs-2012-update-3-1.jpg)

![Visual Studio TFS 2012 Update 3 -2](/assets/images/2013/10/visual-studio-tfs-2012-update-3-2.jpg)

The machine will need to restart. Click on OK to restart.

![Visual Studio TFS 2012 Update 3 -3](/assets/images/2013/10/visual-studio-tfs-2012-update-3-3.jpg)

Another restart needed.

![Visual Studio TFS 2012 Update 3 -4](/assets/images/2013/10/visual-studio-tfs-2012-update-3-4.jpg)

After installation completes, notice that the configuration shows an upgrade wizard since it detects the previous version of TFS (TFS 2012.2).

![Visual Studio TFS 2012 Update 3 -5](/assets/images/2013/10/visual-studio-tfs-2012-update-3-5.jpg?w=660)

The configuration detects the DB. Click on the confirmation of the DB backup. This is very important because **if the TFS update installation fails, you will be unable to restart the update or roll back to the earlier version of TFS without performing a restore procedure**. Click on Next.

![Visual Studio TFS 2012 Update 3 -6](/assets/images/2013/10/visual-studio-tfs-2012-update-3-6.jpg?w=660)

Enter the TFS Service account and its password and click test to verify that they are correct.

![Visual Studio TFS 2012 Update 3 -7](/assets/images/2013/10/visual-studio-tfs-2012-update-3-7.jpg?w=660)

Click on Configure Reporting to configure SSRS for TFS and then click Next.

![Visual Studio TFS 2012 Update 3 -8](/assets/images/2013/10/visual-studio-tfs-2012-update-3-8.jpg?w=660)

Click Populate URLs and then click Next.

![Visual Studio TFS 2012 Update 3 -9](/assets/images/2013/10/visual-studio-tfs-2012-update-3-9.jpg?w=660)

In Specify a TFS Warehouse DB, specify the machine that has the warehouse and click test and then click Next.

![Visual Studio TFS 2012 Update 3 -10](/assets/images/2013/10/visual-studio-tfs-2012-update-3-10.jpg?w=660)
And so the Analysis Service.

![Visual Studio TFS 2012 Update 3 -11](/assets/images/2013/10/visual-studio-tfs-2012-update-3-11.jpg?w=660)

You can choose to use the same account for the TFS Service or enter a separate account (TFSReports).

![Visual Studio TFS 2012 Update 3 -12](/assets/images/2013/10/visual-studio-tfs-2012-update-3-12.jpg?w=660)

Click on Configure SharePoint for SharePoint with TFS and then click Next.

![Visual Studio TFS 2012 Update 3 -13](/assets/images/2013/10/visual-studio-tfs-2012-update-3-13.jpg?w=660)

![Visual Studio TFS 2012 Update 3 -14](/assets/images/2013/10/visual-studio-tfs-2012-update-3-14.jpg?w=660)

Verify the installation and then click Next.

![Visual Studio TFS 2012 Update 3 -15](/assets/images/2013/10/visual-studio-tfs-2012-update-3-15.jpg?w=660)

![Visual Studio TFS 2012 Update 3 -16](/assets/images/2013/10/visual-studio-tfs-2012-update-3-16.jpg?w=660)

![Visual Studio TFS 2012 Update 3 -17](/assets/images/2013/10/visual-studio-tfs-2012-update-3-17.jpg?w=660)

Review Application Tier in the TFS Admin Console to verify it has the new version.

![Visual Studio TFS 2012 Update 3 -18](/assets/images/2013/10/visual-studio-tfs-2012-update-3-18.jpg?w=660)
