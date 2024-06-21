---
layout: post
title: "Configuring Multiple TFS Build Controller on the Same Machine"
date: 2013-01-16 01:39:27 +0100
---

In the previous post ([Understanding Build Controller and Build Agent](https://mohamedradwan-devops.github.ioposts/understanding-build-controller-and-build-agent-for-tfs-team-foundation-server/ "Understanding Build Controller and Build Agent")), I explained that we can't install multiple **Build Controllers** on the same machine. However, there is a workaround or hack that we can use, although it is not supported by Microsoft and not recommended for a production environment. It should only be used for demo machines. Below is a step-by-step video for the post:

{% include embed/youtube.html id='tGyYvdxoJKU' %}

Open the command line as Administrator and create a Windows service and associate it with **TFSBuildServiceHost.exe**. Make sure to leave a space before "=" and you should see success:

```sh
sc create Radwan-Service binPath= "C:\Program Files\Microsoft Team Foundation Server 11.0\Tools\TfsBuildServiceHost.exe /NamedInstance:Radwan-Service" DisplayName= "Radwan-DisplayName"
```



![1-Create-Service-Command-Line](/assets/img/2013/01/1-create-service-command-line-1.jpg)

Open the services to review the created service.

![2-Review-the-service-after-created](/assets/img/2013/01/2-review-the-service-after-created-1.jpg)

Set the Environment Variable for TFS Build Service. 

![3-Set-env-variable](/assets/img/2013/01/3-set-env-variable-1.jpg)


Launch **TfsMgmt.exe** to configure the created build service and click
on **Register**, noticed that it shows that build not configured and
 this for the created service but if we open the **TFS
Administration Console** and navigate to **Build Configuration** we will
find the old service
configured. 

![4-Run-tfsmgmt](/assets/img/2013/01/4-run-tfsmgmt-1.jpg)

![5-Build-Config-for-created-service](/assets/img/2013/01/5-build-config-for-created-service-1.jpg)


Change the port to be different from the running service now, let it be
**9195**. 

![6-Register-Build-Service](/assets/img/2013/01/6-register-build-service-1.jpg)

Create a new **Build Controller** for that
service. 

![7-create-new-build-controller](/assets/img/2013/01/7-create-new-build-controller-1.jpg)


Create a new **Build Agent** for the created **Build
Controller**. 

![8-create-new-build-agent](/assets/img/2013/01/8-create-new-build-agent-1.jpg)

Review the new service with it\'s **Build Controller** and **Build
Agent**.

![9-new-build-service-with-build-controller-and-build-agent](/assets/img/2013/01/9-new-build-service-with-build-controller-and-build-agent-1.jpg)


Review the old service with it\'s **Build Controller** and **Build
Agent**.

![10-old-build-service-with-build-controller-and-build-agent](/assets/img/2013/01/10-old-build-service-with-build-controller-and-build-agent-1.jpg)


Links: 

[Configuring Multiple TFS Build Services on one Machine](http://blogs.msdn.com/b/jimlamb/archive/2010/04/13/configuring-multiple-tfs-build-services-on-one-machine.aspx "Configuring Multiple TFS Build Services on one Machine")

[Scale out Your Build System](http://msdn.microsoft.com/library/dd793166.aspx "Scale out Your Build System")

