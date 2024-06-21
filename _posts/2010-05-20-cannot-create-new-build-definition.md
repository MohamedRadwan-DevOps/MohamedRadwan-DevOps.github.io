---
layout: post
title: "Can't create new build definition in TFS 2010"
date:   2010-05-20 07:40:05 +0100
---


When I start create my first build definition for Team project I face
the following error:

![builError](/assets/img/2010/05/builError.png)

```
TF225001: Creating a build definition requires a build controller be defined for this team project collection. 
There may not be any controller configured or you may not have permission to view them.

```

So after little search I figure it out it will be as the following 

![TFS Admin Console](/assets/img/2010/05/TFS-Admin-Console.png)

![BuildConfiguration](/assets/img/2010/05/BuildConfiguration.png)
 
![BuildConfiguration2](/assets/img/2010/05/BuildConfiguration2.png)

![BuildConfiguration3](/assets/img/2010/05/BuildConfiguration3.png)

So now if you create a new build definition you should see the following screen

![successBuild](/assets/img/2010/05/successBuild.png) 

but the problem that I didn\'t choose network service so I have the following error 
`\"Cannot start service TFSBuildServiceHost on computer\"` and after good search on
event log I found that this because failure of the login so I change it
to be a **network service** as the previous configuration.
