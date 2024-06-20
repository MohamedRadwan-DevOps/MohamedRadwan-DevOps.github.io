---
layout: post
title: "TFS 2013 Access Level for Team Web Access features"
date: 2013-09-30 16:26:48 +0100
---

Using TFS as a client requires a TFS **Client Access License** (CAL). In older versions of TFS (TFS 2010), there was a built-in group called TFS **Work Item Only View** (WIOV) that we could use for all people that we didn’t want to have **CAL**. They would be able to create work items and only see what they created. See the following image from TFS 2010.

![work item only view WIOV](/assets/images/2013/09/work-item-only-view-wiov.jpg)

In **TFS 2012** and **TFS 2013**, this was introduced through **Access Levels**. It also controls the features we want to enable for them, not only from a licensing perspective but also from a security or restriction perspective as well.

![Limited Access TFS 2013](/assets/images/2013/09/limited-access-tfs-2013.jpg?w=660)

![Standard Access TFS 2013](/assets/images/2013/09/standard-access-tfs-2013.jpg?w=660)

![Full Access TFS 2013](/assets/images/2013/09/full-access-tfs-2013.jpg?w=660)

Remember that we can change the default Access Level, so I don’t need to go to Access Level and assign this level every time I create a project.
