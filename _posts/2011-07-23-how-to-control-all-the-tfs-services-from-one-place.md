---
layout: post
title: "How to control all the TFS services from one place"
date:   2011-07-23 21:30:12 +0100
---

We can use the **TFSServiceControl** command to manage, stop or start
all of the services and application pools Visual Studio Team Foundation
Server uses. For example, we use this command when backing up or
restoring databases, or when you are moving your deployment from one
machine to another. Don\'t try to stop the job or any service directly,
the command will be as the following: 

```
TFSServiceControl
\[quiesce\|unquiesce\] 
```

>For more information see the MSDN link [here](http://msdn.microsoft.com/en-us/library/ff470382.aspx "TFS service command line")
{: .prompt-info}

