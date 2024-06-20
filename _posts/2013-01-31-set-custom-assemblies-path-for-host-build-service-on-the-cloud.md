---
layout: post
title: "Set Custom Assemblies Path for Host Build Service on the Cloud"
date: 2013-01-31 05:43:29 +0100
---

This is a very simple post. We know that custom assemblies or third-party libraries must exist on the build server or be checked into source control, and configure the build controller to point to them. But how can we do that with a **Host Build Service** on the cloud? Since we can't put our assemblies on the build machine in the cloud, we need to configure the build controller for the **Hosted Build Service** on the cloud to point to those assemblies. How can we access that control? It's very simple.

Navigate to the Builds page and click on **Actions** -> **Manage Build Controller**.

![BuildNUnit2](/assets/images/2013/01/buildnunit2-1.png)

Select the **Host Build Controller (Virtual)** as we can see in the image, and click on **Properties**.

![BuildNUnit3](/assets/images/2013/01/buildnunit3.png)

Point to your custom assemblies in " **Version control path to custom assemblies**".

![BuildNUnit4](/assets/images/2013/01/buildnunit4.png)

For more info, see the MSDN link here: [Use the hosted build controller](http://tfs.visualstudio.com/en-us/learn/build/hosted-build-controller-in-vs/ "Use the hosted build controller").
