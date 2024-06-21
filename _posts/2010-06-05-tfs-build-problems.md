---
layout: post
title:  "TF215097 Build Service Problems"
date:   2010-06-05 07:40:05 +0100
---

This post can be helpful for all the following error

-   TFS Build Service Problems
-   Build stay in the queue without execute
-   Build controller unavailable
-   there was no endpoint listening at \"TfsBuildAddress\"

When I start to try the Gated Check-in and Continuous Integration -Build
in the MS Build I face a problem that my build stack in the queue
without build and when I drill in I find the following steps that could
help anyone to solve similar problems First you need to click on Manage
Build Controller inside visual studio 2010 

![Click Manage Build Controller](/assets/img/2010/06/openbuildcontroller.png)

Notice what the state of your build controller, if it\'s unavailable or offline? 

![Build Controller State](/assets/img/2010/06/BuildOffileneOrNotWorking.png)

Go to your TFS server and open TFS Administration console 

![Open TFS Administration Consol](/assets/img/2010/06/TFSConsol.png) 

Click on build configuration Sometimes you need to disable and enable the build controller or restart it.

![Build Configuration](/assets/img/2010/06/BuildSettings.jpg)

If you click on the error this will open the event viewer for you, you can check for the error that related to TFSbuildServiceHost 

![Event viewer](/assets/img/2010/06/eventviewer.jpg)

Open  Visual Studio 2010 again and click on Manage Build Controller, you
should see build controller available and ready for work 

![Build available](/assets/img/2010/06/buildenable.png)
