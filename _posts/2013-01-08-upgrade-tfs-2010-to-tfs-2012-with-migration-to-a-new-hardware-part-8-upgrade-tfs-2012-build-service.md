---
layout: post
title: "Upgrade TFS 2010 to TFS 2012 with Migration to a New Hardware - Part 8 - Upgrade TFS 2012 Build Service"
date: 2013-01-08 01:18:26 +0100
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

[https://upgradetfs2010totfs2012.codeplex.com/](https://upgradetfs2010totfs2012.codeplex.com/ "Upgrading TFS 2010 to TFS 2012 with Migration to a New Hardware")
[![](https://mg2otq.sn2.livefilestore.com/y1mmcQSYrLWQ757Pb1cWnVdzrBuwKP3r3jPo9VnNct09pHE2cGb25cQr7MQNHyLZrBBfu2vzrT5z46XyIVYeKm9V_svUZwzlwAzOyU2_lcx_X_0Qs1Inh2pag/CodePlex.png?psid=1 "Test Uitities on CodePlex"){width="332" height="88"}](https://upgradetfs2010totfs2012.codeplex.com/ " Upgrading TFS 2010 to TFS 2012 with Migration to a New Hardware Guide")

---

**Part 8 - Upgrade TFS 2012 Build Service**

1. **Uninstall TFS 2010 Build Service**
2. **Install TFS 2012 Build Service**
3. **Configure TFS 2012 Build Service**

The following is the video that explains this blog post:

{% include embed/youtube.html id='shBsglrFp34' %}

**Uninstall TFS 2010 Build Service**

1. Open the Control Panel on the server where the TFS 2010 Build Service is installed.
2. Navigate to "Programs and Features."
3. Locate "Team Foundation Build Service 2010" in the list of installed programs.
4. Select it and click "Uninstall."
5. Follow the prompts to complete the uninstallation.

![75-uninstall-build-service](/assets/images/2013/01/75-uninstall-build-service.jpg?w=660)

**Install TFS 2012 Build Service**

1. Download the TFS 2012 installation media from the official Microsoft website.
2. Run the installation executable on the server where you want to install the TFS 2012 Build Service.
3. Follow the prompts in the installation wizard.
4. Select "Team Foundation Build Service" from the list of components to install.
5. Complete the installation.

![76-install-build-service](/assets/images/2013/01/76-install-build-service.jpg?w=660)

**Configure TFS 2012 Build Service**

1. Open the TFS Administration Console on the server where the TFS 2012 Build Service is installed.
2. Navigate to the "Build Configuration" section.
3. Click "Configure Installed Features."
4. Follow the prompts to configure the Build Service, specifying the TFS server and project collection it should use.
5. Complete the configuration and verify that the Build Service is running correctly.

![77-configure-build-service](/assets/images/2013/01/77-configure-build-service.jpg?w=660)

Review the success of the installation and configuration.

![78-review-success](/assets/images/2013/01/78-review-success.jpg?w=660)

By following these steps, you can successfully upgrade your TFS 2010 Build Service to TFS 2012 and ensure that your build environment is running the latest version.

