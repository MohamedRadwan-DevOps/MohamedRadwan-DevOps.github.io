---
layout: post
title: "Upgrade TFS 2008 to TFS 2013 Update-2 step-by-step"
date: 2014-06-08 11:23:40 +0100
---

In this post I will explain a step-by-step walk through on how to upgrade **TFS2008** to [**TFS2013 Update-2**](http://support.microsoft.com/kb/2927432 "Description of Visual Studio 2013 Update 2 - Microsoft Support"). Here is the flow of the walk through:

![Drawing2](/assets/img/2014/05/drawing2.jpg)

Here are the steps:

### TFS2008

Backup TFS2008 databases or just get them offline so you can copy them:

![1-backup tfs 2008 database](/assets/img/2014/06/1-backup-tfs-2008-database.jpg)

Copy Data Files To Data Folder Or Backup Files To Backup Folder on the Data Tire for TFS2012:

![2-copy data files to data folder or backup files to backup folder](/assets/img/2014/06/2-copy-data-files-to-data-folder-or-backup-files-to-backup-folder.jpg)

### TFS2012

Open SQL Management Studio From Data Tire for TFS2012:

![3-open sql management studio from data tire of TFS](/assets/img/2014/06/3-open-sql-management-studio-from-data-tire-of-tfs.jpg)

Attach Data Files or Restore Backup Files If You Made Backup:

![5-attach all the following databases](/assets/img/2014/06/5-attach-all-the-following-databases.jpg)

Attach All the Following Databases:

![6-we can see the attached databases as the following](/assets/img/2014/06/6-we-can-see-the-attached-databases-as-the-following.jpg)
Open TFS2012 Administration Console:

![7-open tfs 2012 administration console](/assets/img/2014/06/7-open-tfs-2012-administration-console.jpg)

Click on Configure Installed Features:

![8-click on configure installed features](/assets/img/2014/06/8-click-on-configure-installed-features.jpg)

Choose Upgrade and then click Next:

![9-choose upgrade tab in tfs administration console and click start wizard](/assets/img/2014/06/9-choose-upgrade-tab-in-tfs-administration-console-and-click-start-wizard.jpg)

![10](/assets/img/2014/06/10.jpg)

In the Databases section, make sure you select **TfsIntegration** and you checked the check box to confirm you have a backup:

![11-list available database for tfs](/assets/img/2014/06/11-list-available-database-for-tfs.jpg)

In the Account section use the default for the service account (Network Service):

![12-use network service as a service account](/assets/img/2014/06/12-use-network-service-as-a-service-account.jpg)

![13](/assets/img/2014/06/13.jpg)

If your installation of TFS2008 includes Reporting like mine, click on Configure Reporting for use with TFS:

![14-configure reporting to use with team foundation server](/assets/img/2014/06/14-configure-reporting-to-use-with-team-foundation-server.jpg)

In my case I needed to choose the secure one as this is what we have:

![15-provide the reporting services settings for team foundation server](/assets/img/2014/06/15-provide-the-reporting-services-settings-for-team-foundation-server.jpg)

In the Analysis Service, type the name of the machine and click Test:

![16](/assets/img/2014/06/16.jpg)

In Report Reader Account put the service account for reporting service and click Test:

![17-tfs reporting services reader account](/assets/img/2014/06/17-tfs-reporting-services-reader-account.jpg)

If you have SharePoint click on Configure SharePoint for use with TFS:

![18-configure sharepoint use with team foundation server](/assets/img/2014/06/18-configure-sharepoint-use-with-team-foundation-server.jpg)

Name the collection, I choose TFS2008_Collection:

![19-Enter the name of the collection](/assets/img/2014/06/19-enter-the-name-of-the-collection.jpg)

Configure the upgrade and review the success:

![19-2](/assets/img/2014/06/19-2.jpg)

Review your team projects in the TFS2008_Collection:

![20-examine the old team projects](/assets/img/2014/06/20-examine-the-old-team-projects.jpg)

Detach the collection:

![21-tfs 2008 detach collection](/assets/img/2014/06/21-tfs-2008-detach-collection.jpg)

![22-upgrade to tfs 2013](/assets/img/2014/06/22-upgrade-to-tfs-2013.jpg)

If there is any warning, review it and complete the detach process:

![23](/assets/img/2014/06/23.png)

![24](/assets/img/2014/06/24.jpg)

Backup The TFS2008_Collection DB:

![25-backup tfs2008 collection](/assets/img/2014/06/25-backup-tfs2008-collection.jpg)

![25-backup tfs2008 collection-2](/assets/img/2014/06/25-backup-tfs2008-collection-2.jpg)

Copy the backup file to the new **TFS2013** Server:

![26-copy the collection backup to TFS 2013 DT Data tier](/assets/img/2014/06/26-copy-the-collection-backup-to-tfs-2013-dt-data-tier.jpg)

### TFS2013

Open SQL Management Studio From the Data Tire for the **TFS2013**:

![27-open sql management on TFS data tier](/assets/img/2014/06/27-open-sql-management-on-tfs-data-tier.jpg)

Attach the Backup of TFS2008_Collection DB:

![28-attach tfs 2008 collection to tfs 2013](/assets/img/2014/06/28-attach-tfs-2008-collection-to-tfs-2013.jpg)

![28-attach tfs 2008 collection to tfs 2013-2](/assets/img/2014/06/28-attach-tfs-2008-collection-to-tfs-2013-2.jpg)

Open TFS2013 Administration Console:

![28-2](/assets/img/2014/06/28-21.jpg)
Click Team Projects Collections and then click on Attach Collection:

![29-Open Team Foundation Server Administration Console](/assets/img/2014/06/29-open-team-foundation-server-administration-console.jpg)

Click on **List Available Databases**, you should see the restored TFS2008_Collection DB, check to confirm that you have a backup of that database and click Next:

![30-List Available Dtabases](/assets/img/2014/06/30-list-available-dtabases.jpg)

Name the collection, I choose TFS2008_Collection:

![31-Provide a Collection Name and Description](/assets/img/2014/06/31-provide-a-collection-name-and-description.jpg)

Review and then configure:

![32-Review the confiuration and Verify](/assets/img/2014/06/32-review-the-confiuration-and-verify.jpg)

![33-Attach the collection](/assets/img/2014/06/33-attach-the-collection.jpg)

![34-Monitor the Team Project Collection attach porgress](/assets/img/2014/06/34-monitor-the-team-project-collection-attach-porgress.jpg)

Review the migrated team projects in the TFS2008_Collection:

![35-Review migrated collection and projects](/assets/img/2014/06/35-review-migrated-collection-and-projects.jpg)

Done! [For more information about versions and options for TFS upgrade](http://blogs.msdn.com/b/tfssetup/archive/2013/01/30/tfs-2012-upgrade-options.aspx "more information about versions and options for TFS upgrade")
