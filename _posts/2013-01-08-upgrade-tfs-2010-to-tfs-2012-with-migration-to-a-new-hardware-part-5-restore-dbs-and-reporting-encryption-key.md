---
layout: post
title: "Upgrade TFS 2010 to TFS 2012 with Migration to a New Hardware - Part 5: Restore DBs and Reporting Encryption Key"
date: 2013-01-08 01:17:20 +0100
---

In this blog series, I start to explain a step-by-step tutorial on how to upgrade an existing TFS 2010 to [TFS 2012 Update 1](http://msdn.microsoft.com/en-us/vstudio/ff637362.aspx) with the migration to new hardware. The series will include videos and images as well. In the last post, I will include one video that collects all parts for a one-shot view. This series consists of the following parts:

- [Part 1 - Introduction.](https://mohamedradwan-devops.github.io/posts/upgrade-tfs-2010-to-tfs-2012-with-migration-to-a-new-hardware-series/ "Part 1 - Introduction.")
- [Part 2 - Prepare SharePoint for the new system.](https://mohamedradwan-devops.github.io/posts/upgrade-tfs-2010-to-tfs-2012-with-migration-to-a-new-hardware-part-2-prepare-sharepoint-for-the-new-system/ "Part 2 - Prepare SharePoint for the new system.")
- [Part 3 - Prepare the new machine and install SQL Server.](https://mohamedradwan-devops.github.io/posts/upgrade-tfs-2010-to-tfs-2012-with-migration-to-a-new-hardware-part-3-prepare-the-new-machine-and-install-sql-server/ "Part 3 - Prepare the new machine and install SQL Server.")
- [Part 4 - Install TFS 2012 Update 1 & Backup DBs and Reporting Key.](https://mohamedradwan-devops.github.io/posts/upgrade-tfs-2010-to-tfs-2012-with-migration-to-a-new-hardware-part-4-install-tfs-2012-update-1-backup-dbs-and-reporting-key/ "Part 4 - Install TFS 2012 Update 1 & Backup DBs and Reporting Key.")
- [Part 5 - Restore DBs and Reporting Encryption Key.](https://mohamedradwan-devops.github.io/posts/upgrade-tfs-2010-to-tfs-2012-with-migration-to-a-new-hardware-part-5-restore-dbs-and-reporting-encryption-key/ "Part 5 - Restore DBs and Reporting Encryption Key.")
- [Part 6 - Configure TFS 2012.](https://mohamedradwan-devops.github.io/posts/upgrade-tfs-2010-to-tfs-2012-with-migration-to-a-new-hardware-part-6-configure-tfs-2012/ "Part 6 - Configure TFS 2012.")
- [Part 7 - Verify upgrade success and other configuration.](https://mohamedradwan-devops.github.io/posts/upgrade-tfs-2010-to-tfs-2012-with-migration-to-a-new-hardware-part-7-verify-upgrade-success-and-other-configuration/ "Part 7 - Verify upgrade success and other configuration.")
- [Part 8 - Upgrade TFS 2012 Build Service.](https://mohamedradwan-devops.github.io/posts/upgrade-tfs-2010-to-tfs-2012-with-migration-to-a-new-hardware-part-8-upgrade-tfs-2012-build-service/ "Part 8 - Upgrade TFS 2012 Build Service.")
- [Part 9 - Summary.](https://mohamedradwan-devops.github.io/posts/upgrade-tfs-2010-to-tfs-2012-with-migration-to-a-new-hardware-part-9-summary/ "Part 9 - Summary.")

Each part consists of one or many sections as needed.

---

**Part 5 - Restore DBs and Reporting Encryption Key**

- **Run TFS 2012 Restore Tool and restore old DBs to the new SQL Server 2012.**
- **Change Reporting DB and restore Reporting Encryption Key.**

The following is the video that explains this blog post.

{% include embed/youtube.html id='shBsglrFp34' %}


**Run TFS 2012 Restore Tool and restore old DBs to the new SQL Server 2012**

In this section, I will explain how to restore the backup DBs to the new **SQL Server 2012** using the new tools [**TFSRestore.exe**](http://msdn.microsoft.com/en-us/library/jj620932.aspx "Back up and Restore Data for TFS").

Get back to the command line on the new machine (**TFS 2012**), type **TFSRestore** and then enter.

![46-Run-TFSRestore](/assets/img/2013/01/46-run-tfsrestore-1.jpg)

The TFS restore tool will launch.

![47-Connect-TFS12UP](/assets/img/2013/01/47-connect-tfs12up-1.jpg)

Click **Connect** and in the **Select Backup Location**, add the shared folder that has been created earlier and now has all backup files, select all DBs, and check **Overwrite the existing database(s)** to replace the existing **Reporting Service DB**, otherwise the restore will fail.

![48-Add-shared-folder-of-DBs](/assets/img/2013/01/48-add-shared-folder-of-dbs.jpg)

Review the success of the restore.

![49-TheData-Restored-successfully](/assets/img/2013/01/49-thedata-restored-successfully-1.jpg)

**Change Reporting DB and restore Reporting Encryption Key**

Open the **Reporting Service Configuration Manager**.

![50-1-Open-Report-Service-Config-on-TFS2012](/assets/img/2013/01/50-1-open-report-service-config-on-tfs2012.jpg)

Click **Connect** to the new server (**TFS12UP**), then click on the **Database** tab and then click on [**Change Database**](http://msdn.microsoft.com/en-us/library/bb630434.aspx "Change Database Wizard").

![50-Click-Database-change](/assets/img/2013/01/50-click-database-change.jpg)

Select **Choose an existing report server database** and then click **Next**.

![51-Choose an existing report](/assets/img/2013/01/51-choose-an-existing-report.jpg)

Test the connection to the server and then click **Next**.

![52-test connection](/assets/img/2013/01/52-test-connection.jpg)

Select the **Report Server** database from the drop-down and then click **Next**.

![53-select-report-server-db](/assets/img/2013/01/53-select-report-server-db.jpg)

In **Authentication Type**, leave the default (**Service Credential**) and then click **Next**.

![54-select-service-credentials](/assets/img/2013/01/54-select-service-credentials.jpg)

In **Summary**, review and click **Next**.


![55-summary](/assets/img/2013/01/55-summary-1.jpg)

Review the success of changing the DB.

![56-change-report-DB-success](/assets/img/2013/01/56-change-report-db-success.jpg)

Click on the **Encryption Keys** tab and then click on the **Restore** button, select the shared folder path that has the backup key, type the password that we used during the key backup, and click **OK**.

![57-Restore-key](/assets/img/2013/01/57-restore-key.jpg)

Review the success of restoring the key.

![58-MakeSure-Restore-success](/assets/img/2013/01/58-makesure-restore-success-1.jpg)

Click on [**Scale-out Deployment**](http://msdn.microsoft.com/en-us/library/ms156453(v=sql.105).aspx "Configuring Reporting Services for Scale-Out Deployment"), select the old TFS machine (**TFS2010**) and click on **Remove Server**. If you have the same error as me, you will need to remove that manually.

![59-Try-to-remove-TFS2010-from-Scale-out](/assets/img/2013/01/59-try-to-remove-tfs2010-from-scale-out-1.jpg)

Go to the SQL Server **RSKeyMgmt Tool** folder and copy the path "**C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Binn**".

![60-copy-path-of-key-tool](/assets/img/2013/01/60-copy-path-of-key-tool-1.jpg)

Open the command line tool as **Administrator**, type **cd** and paste the path of the tool.

![61-type-cd-past-folder-path](/assets/img/2013/01/61-type-cd-past-folder-path-1.jpg)

Type **RSKeyMgmt -l** to list all servers with their GUIDs.

![62-Run-RSKey-list-all](/assets/img/2013/01/62-run-rskey-list-all-1.jpg)

Copy the **GUID** of the old server (**TFS2010**), type **RSKeyMgmt -r** and paste the **GUID** to remove this server, then list again to make sure that the server was successfully removed.

![63-remove-with-GUID](/assets/img/2013/01/63-remove-with-guid-1.jpg)

Review the **Scale-out Deployment** to make sure it's removed.

![64-make-sure-it-removed](/assets/img/2013/01/64-make-sure-it-removed-1.jpg)
