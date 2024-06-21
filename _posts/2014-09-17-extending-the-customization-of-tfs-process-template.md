---
layout: post
title: "Extending the customization of TFS Process Template"
date: 2014-09-17 22:30:44 +0100
---

We can customize [TFS process template](http://msdn.microsoft.com/en-us/library/ms400752.aspx "Work with team project artifacts, choose a process template") by [modifying the definition for different process template](http://msdn.microsoft.com/en-us/library/ms194980.aspx "Define and modify work item fields") items (XML files), like Work-Items, Process Configuration, Categories, Global List, Global Workflow, etc. The XML customization includes:

- Adding more fields
- Adding more rules
- Adding more states
- Modifying many configurations for how the displaying and the performing of TWA ([Team Web Access](http://msdn.microsoft.com/en-us/library/ee523998.aspx "Work in Team Web Access"))

This could give us many possibilities, but sometimes we need more than just adding fields or rules. Sometimes we need real programming capabilities, such as getting the current value from a Work-Item and putting it in another Work-Item, or just calculating some Work-Items values together, or changing a Work-Item's field based on a change from a field in another Work-Item. So how can we do that?

## [We have 3 options:]{style="color:#339966;"}

#### 1. We can use a TFS server-side plugin which runs within the application pool of the TFS

[How to create a TFS Server Side Plugin](https://mohamedradwan-devops.github.io/posts/subscribe-to-tfs-event-handler-using-a-tfs-plugin/ "How to create TFS Server Side Plugin")

#### 2. Register a web service by subscribing for TFS Service that is based on SQL Server notification

[How to Subscribe to TFS Event Model](https://mohamedradwan-devops.github.io/posts/how-to-subscribe-to-tfs-event-model/ "How to Subscribe to TFS Event Model")

#### 3. We can also create a custom control that does that. However, this will not work for TWA (Team Web Access) or in Excel or any other client unless we create a custom control for TWA and find a way for other clients as well.

[Custom Controls for TFS Work Item Tracking](https://witcustomcontrols.codeplex.com/wikipage?title=MultiValue%20Control "Custom Controls for TFS Work Item Tracking")

For more information, see [Adding field to a requirement work item that gets its value from a child item](http://social.msdn.microsoft.com/Forums/vstudio/en-US/c6860a0a-8e2a-4732-8624-705bda384b62/adding-field-to-a-requirement-work-item-that-gets-its-value-from-a-child-item?forum=tfsprocess).
