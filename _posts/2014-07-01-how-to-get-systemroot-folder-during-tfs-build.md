---
layout: post
title: "How to get SystemRoot folder during TFS Build"
date: 2014-07-01 06:57:59 +0100
---

Getting the System Root Directory during TFS Build was not straightforward as I thought, so I decided to share my experience on how to get that.

- I used the **InvokeMethod** activity. In the **Target Type**, I will put the name of the static class that has the method I need to use.
- In **MethodName**, I will put **GetEnviornmentVariable**.
- Write the value to the build log by calling **WriteBuildError** and passing the value returned from **GetEnviornmentVariable**.

![6-25-2014 12-53-38 PM](/assets/img/2014/06/6-25-2014-12-53-38-pm.jpg)

![6-25-2014 12-58-59 PM](/assets/img/2014/06/6-25-2014-12-58-59-pm.jpg)

Note: For **InvokeMethod** activity, if I need to call a method from an instance object, then I will use **Target Object** not **Target Type**.
