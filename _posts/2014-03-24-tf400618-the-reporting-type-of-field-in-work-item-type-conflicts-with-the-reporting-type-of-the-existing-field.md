---
layout: post
title: "TF400618: The reporting type of field in work item type conflicts with the reporting type of the existing field."
date: 2014-03-24 00:46:21 +0100
---

When I upgraded a server from TFS 2010 to TFS 2013, I faced the following error: 

>There are no process templates available with valid configuration settings for this team project.
TF400618: The reporting type of field "Field name" in work item type "Work-Item type" conflicts with the reporting type of the existing field.
{: .prompt-danger}

![TF400618](/assets/img/2014/03/tf400618.png)

This problem occurs because the old project used a field as **[reportable="dimension"]** but the new process template (Scrum 2013) doesn't. So, all I needed to do was:

1. Download the Scrum Process Template from TFS 2013.
2. Update the field to be reportable="dimension".
3. Upload the process template and override the existing one.

So now the two fields are matching, and it succeeded.
