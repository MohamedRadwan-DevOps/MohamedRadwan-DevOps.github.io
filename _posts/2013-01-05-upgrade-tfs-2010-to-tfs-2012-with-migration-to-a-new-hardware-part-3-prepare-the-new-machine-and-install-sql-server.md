---
layout: post
title: "Upgrade TFS 2010 to TFS 2012 with Migration to a New Hardware - Part 3: Prepare the new machine and install SQL Server"
date: 2013-01-05 15:35:33 +0100
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

All the series were enhanced and featured as a Complete Guide for **Upgrading TFS 2010 to TFS 2012 with Migration to a New Hardware**. 

![Book 3d-all-2 copy](/assets/images/2013/11/book-3d-all-2-copy.jpg?w=660)

[Upgrading TFS 2010 to TFS 2012 with Migration to a New Hardware Guide on CodePlex](https://upgradetfs2010totfs2012.codeplex.com/)

[![CodePlex](https://mg2otq.sn2.livefilestore.com/y1mmcQSYrLWQ757Pb1cWnVdzrBuwKP3r3jPo9VnNct09pHE2cGb25cQr7MQNHyLZrBBfu2vzrT5z46XyIVYeKm9V_svUZwzlwAzOyU2_lcx_X_0Qs1Inh2pag/CodePlex.png?psid=1 "Test Utilities on CodePlex")](https://upgradetfs2010totfs2012.codeplex.com/ "Upgrading TFS 2010 to TFS 2012 with Migration to a New Hardware Guide")
