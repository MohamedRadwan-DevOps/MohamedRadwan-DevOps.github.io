---
layout: post
title: "Upgrade TFS 11 Beta Failure and Its Solution"
date:   2012-03-06 08:26:48 +0100
---

When I started upgrading [TFS 2010](https://mohamedradwan-devops.github.io/category/alm/tfs/ "TFS links") to [TFS 11 Beta](https://mohamedradwan-devops.github.io/category/visual-studio-11-beta/ "TFS 11 Beta") (Visual Studio 11 Beta Team Foundation Server), I encountered the following error:

> Package (tfs_objectmodel_x64) caching failed with the following status 0x80070001.  
> Package caching failed. Check individual package cache errors for more information.  
> Installation failed. Check individual package installation errors for more information.

As shown in the following image:

[![TFS 11 Beta error in upgrade](/assets/img/2012/03/TFS-11-Beta-error-in-upgrade-1024x507.png)](/assets/img/2012/03/TFS-11-Beta-error-in-upgrade.png)

When I checked the log, I found the following error line in the log file:

> [Error 0x80070001: Failed attempt to copy payload from: 'D:\packages\TFSObjectModel\x64\TFSObjectModel-x64.msi' to:  
> C:\Users\mradwan\AppData\Local\Temp\2\{519da648-4da6-44e1-af66-effd6d65f194}\tfs_objectmodel_x64.]

When I tried to manually copy "tfs_objectmodel_x64", it failed. So, I extracted the ISO again from the source and tried to copy it. It worked, but when I tried to set up TFS 11 Beta again, it gave me the same error but with different log information this time. It was as follows:

> [Error 0x800b0003: Failed authenticode verification of payload:  
> C:\ProgramData\Package Cache\.unverified\tfs_objectmodel_x64]

### Solution:

So I knew it was a corrupted file. I downloaded the TFS 11 Beta again, and the next step worked fine.
