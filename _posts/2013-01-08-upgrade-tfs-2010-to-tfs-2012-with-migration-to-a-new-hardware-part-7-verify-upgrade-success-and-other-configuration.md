---
layout: post
title: "Upgrade TFS 2010 to TFS 2012 with Migration to a New Hardware - Part 7 - Verify upgrade success and other configuration"
date: 2013-01-08 01:18:00 +0100
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

All the series was enhanced and featured as a Complete Guide for **Upgrading TFS 2010 to TFS 2012 with Migration to a New Hardware**.

![Book 3d-all-2 copy](/assets/img/2013/11/book-3d-all-2-copy.jpg)

[https://upgradetfs2010totfs2012.codeplex.com/](https://upgradetfs2010totfs2012.codeplex.com/ "Upgrading TFS 2010 to TFS 2012 with Migration to a New Hardware")
[![](https://mg2otq.sn2.livefilestore.com/y1mmcQSYrLWQ757Pb1cWnVdzrBuwKP3r3jPo9VnNct09pHE2cGb25cQr7MQNHyLZrBBfu2vzrT5z46XyIVYeKm9V_svUZwzlwAzOyU2_lcx_X_0Qs1Inh2pag/CodePlex.png?psid=1 "Test Uitities on CodePlex"){width="332" height="88"}](https://upgradetfs2010totfs2012.codeplex.com/ " Upgrading TFS 2010 to TFS 2012 with Migration to a New Hardware Guide")

---

**Part 7 - Verify upgrade success and other configuration**

1. **Verify TFS Upgrade Success**
2. **Verify SharePoint Integration**
3. **Verify Reporting Integration**
4. **Configure Additional Settings**

The following is the video that explains this blog post:

{% include embed/youtube.html id='shBsglrFp34' %}

**Verify TFS Upgrade Success**

Open the TFS 2012 Administration Console and check the status of the Application Tier, Reporting, and SharePoint Extensions to ensure they are running correctly.

![70-verify-tfs-success](/assets/img/2013/01/70-verify-tfs-success.jpg)

**Verify SharePoint Integration**

Open the SharePoint Central Administration, navigate to the TFS integration settings, and verify that the TFS extensions are correctly configured and running.

![71-verify-sharepoint](/assets/img/2013/01/71-verify-sharepoint.jpg)

**Verify Reporting Integration**

Open SQL Server Reporting Services, navigate to the TFS reports, and ensure that the reports are accessible and running correctly.

![72-verify-reporting](/assets/img/2013/01/72-verify-reporting.jpg)

**Configure Additional Settings**

Configure any additional settings as needed, such as adjusting user permissions, setting up additional integrations, or configuring backups.

![73-configure-additional-settings](/assets/img/2013/01/73-configure-additional-settings.jpg)

Review the success of all configurations.

![74-config-success](/assets/img/2013/01/74-config-success.jpg)
