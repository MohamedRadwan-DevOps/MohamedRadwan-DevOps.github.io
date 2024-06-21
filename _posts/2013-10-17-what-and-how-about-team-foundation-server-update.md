---
layout: post
title: "What and How about Team Foundation Server Update"
date: 2013-10-17 22:26:19 +0100
---

![TFS Update](/assets/img/2013/10/tfs-update.jpg)

I just want to highlight that Visual Studio and Team Foundation Server (TFS) installation mechanics are different. The Visual Studio update installs on top of whatever is already installed on the computer, so you will find **Visual Studio Update N** media or installation file. Most of Visual Studio updates are cumulative releases that include the new features and fixes that were delivered in previous releases. The TFS update is a full layout that replaces whatever is installed on the computer, so you will always find **TFS with Update N media**. Before you try to apply the TFS update, make sure that you have a full backup of your current databases. **If the TFS update installation fails, you will be unable to restart the update or roll back to the earlier version of TFS without performing a restore procedure**.

To simplify the meaning, just think of TFS update as if it’s a new version of TFS so it’s upgrading the existing one and this is the reason after you install the update you will find the configuration shows you the upgrade wizard. For example, see the following post about how to Install TFS 2012 Update 3 [Install and configure TFS 2012 Update 3 (TFS 2012.3)](https://mohamedradwan-devops.github.io/posts/install-and-configure-tfs-2012-update-3-tfs-2012-3/ "Install and configure TFS 2012 Update 3 (TFS 2012.3)").
