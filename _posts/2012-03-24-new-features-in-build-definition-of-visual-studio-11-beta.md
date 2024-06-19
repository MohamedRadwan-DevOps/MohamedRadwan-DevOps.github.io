---
layout: post
title: "New Features in Build Definition of Visual Studio 11 Beta"
date:   2012-03-24 00:01:15 +0100
---

After I [upgrade my build server 2010 to build service 11 beta](https://mohamedradwan-devops.github.io/posts/install-or-upgrade-tfs-build-service-11-beta-on-a-separate-build-server/ "Upgrade TFS build service")
I just try the build definition and I found new features that give us
more control over the build process.

-   Queuing options.
-   Drop Folder.

-   Queuing options.

We have 3 options (Enabled, Paused, Disabled) as the following image:

[![](/assets/images/2012/03/General-1024x543.png)](/assets/images/2012/03/General.png)


-   Drop Folder.

We have also 3 options (Don\'t copy, Copy to UNC, Copy to
source control). 

[![Queue Options](/assets/images/2012/03/Build-Defaults-1024x558.png)](/assets/images/2012/03/Build-Defaults.png)

-   Don\'t copy.

We can use this when we don\'t need the build binaries (CI).

-   Copy to UNC.

We can use this when we want the binaries and we want
it available inside our corporate LAN.

-   Copy to source control.

We can use this when we want the binaries and we want it to
be available for all people that has access to TFS source control, so
they may didn\'t have access to LAN but they have access to TFS source
control.

