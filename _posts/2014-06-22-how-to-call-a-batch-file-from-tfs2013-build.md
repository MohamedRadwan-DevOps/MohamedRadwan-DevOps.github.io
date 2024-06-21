---
layout: post
title: "How to Call a batch file from TFS2013 Build?"
date: 2014-06-22 21:38:46 +0100
---

I run into a situation which needed to run a batch file from [TFS Build](http://msdn.microsoft.com/en-us/library/ms181710(v=vs.90).aspx "Team Foundation Build Overview"), this batch file downloads some files from a file server and I just needed to copy those files later during the same build process to another machine. I will simulate that by creating a batch file that creates a file and copies the created file to another machine. Here is the batch file that creates a new text file:

![6-22-2014 10-19-33 PM](/assets/img/2014/06/6-22-2014-10-19-33-pm.jpg)

If I just double-click on that file, it will create a new file called NewFile.txt:

![6-18-2014 11-22-07 AM](/assets/img/2014/06/6-18-2014-11-22-07-am.jpg)

1. Open any **Build Process Template** and delete all its activities.
2. Add **Sequence** Activity with name: **Overall Build Process**.
3. Drag and drop [**GetBuildDetail**](http://msdn.microsoft.com/en-us/library/gg265783.aspx#Activity_GetBuildDetail "Get a reference to the IBuildDetail object (GetBuildDetail activity)") Activity inside the **Sequence** Activity.
4. Drag and drop **AgentScope** Activity with name: **Run on Agent**.
5. Drag and drop **GetBuildDirectory** Activity inside **AgentScope** Activity.
6. Drag and drop **InvokeProcess** Activity with name: **Call a batch file**.
7. Declare a variable of type [**IBuildDetail**](http://msdn.microsoft.com/en-us/library/microsoft.teamfoundation.build.client.ibuilddetail.aspx "IBuildDetail Interface") with name: **MyBuildDetail**, and assign the return value from **[GetBuildDetail](http://msdn.microsoft.com/en-us/library/gg265783.aspx#Activity_GetBuildDetail "Get a reference to the IBuildDetail object (GetBuildDetail activity)")** to it.
8. Declare a variable of type **String** with name: **MyBuildDirectory**, and assign the return value from **GetBuildDirectory** to it. 

[More information on how to assign a value to a variable from the return execution of an activity](https://mohamedradwan-devops.github.io/posts/how-to-copy-build-output-to-a-lab-environment-machine-for-tfs2013/ " JUNE 22, 2014 BY MOHAMED RADWAN (MVP) How to Copy Build output to a Lab Environment Machine for TFS2013").

![6-18-2014 10-33-40 AM](/assets/img/2014/06/6-18-2014-10-33-40-am.jpg)

We need to include the folder that contains the script or the batch file in the Source Settings of our **Build Definition**, so the build server copies it in the working directory of the build. But first, let's remember what is the working directory of the build. It's a folder like a temp folder the build process uses to get the last changeset so it could build it. We configure that from **TFS Administration Console** for the agent:

![6-18-2014 11-16-11 AM](/assets/img/2014/06/6-18-2014-11-16-11-am.jpg)

So we will need to include the folder that contains the script or the batch file in the Source Settings of our **Build Definition**:

![6-18-2014 11-13-02 AM](/assets/img/2014/06/6-18-2014-11-13-02-am.jpg)

So now if we run this build, we will find that it gets the last changeset including the script:

![6-18-2014 11-17-43 AM](/assets/img/2014/06/6-18-2014-11-17-43-am.jpg)

So now I can give the **InvokeProcess** Activity the path on the working directory as the following:

![6-18-2014 11-02-17 AM](/assets/img/2014/06/6-18-2014-11-02-17-am.jpg)

Remember if I run the build, the file will not be created in the related path, but it will be in **System 32** folder:

![6-18-2014 11-21-38 AM](/assets/img/2014/06/6-18-2014-11-21-38-am.jpg)

Then I will need to copy that file to the needed machine, see the following post for typical steps: [How to Copy Build output to a Lab Environment Machine for TFS2013](https://mohamedradwan-devops.github.io/posts/how-to-copy-build-output-to-a-lab-environment-machine-for-tfs2013/ "How to Copy Build output to a Lab Environment Machine for TFS2013")
