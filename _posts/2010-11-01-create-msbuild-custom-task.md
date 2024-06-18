---
layout: post
title:  "Create MSBuild Custom Task"
date:   2010-11-01 07:40:05 +0100
---

Hello, I Will show you how to create MSBuild custom task I know you will find many examples on the internet but if you just try most of them most properly it will not work, so I decide to post article that describe it in very simple way with source code of the success project. If you want to see a tutorial on MSBuild you can visit the following link
[click-here](https://mohamedradwan-devops.github.io/2010/10/15/msbuild-tutorial/ "MSBuild Tutorial")

First part

-   Create a class library project that will contain all your custom
    task classes
-   Reference both Microsoft.Build.Framework and
    Microsoft.Build.Utilities
-   Create a new class and name it MyTask inherit from Class Task, and
    override the Execute method
-   Call Log.LogMessage to output a message during the build and give it
    the property of your class

```c#

using System;
using Microsoft.Build.Framework;
using Microsoft.Build.Utilities;

namespace CustomTask 
{
    public class MyTask : Task 
    {
        public string MyProperty { get; set; }

        public override bool Execute() 
        {
            // Log a high-importance comment
            Log.LogMessage(MessageImportance.High, "The task was passed \"" + MyProperty + "\".");
            return true;
        }
    }
}

```

-   Create any project,  it prefers to be class library also and remove all the code between the project element
-   Edit the target to be MyTarget
-   Add a reference to the assembly that contain the custom task and here what cause the problem to happen, the wrong path always make problem so my advice to you that you have to know exactly how to point to specific file and what is the different between absolute and relative path, how to out from the current folder or 2 folders and so on so forth, any way you just add the reference

<!-- -->

- Add new Target called MyTarget and start using the task

[![Use your custom task](/assets/images/2010/10/ProjectFile.png)](/assets/images/2010/10/ProjectFile.png)


- Open Visual studio CMD and go the project file path and run MSBuild and that\'s it

[![Run MSBuild for the project](/assets/images/2010/10/CMD.png)](/assets/images/2010/10/CMD.png)

- Run MSBuild for the project\[/caption\] To download the project just click [here](http://cid-4bcaa16d27b46600.office.live.com/self.aspx/Blog%20New%20Docs%20only/UseTask.zip "CustomTask Project")
  
- You can find also the link on the MSDN that describe the custom task [here](http://msdn.microsoft.com/en-us/library/t9883dzc.aspx "MSDN")

> Most of problem happen because the path of the dll of the custom task so if you have a problem creating your own you just use absolute path to make sure the example work and then fix the absolute path with relative path I hope you like it.
{: .prompt-danger }


