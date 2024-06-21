---
layout: post
title: "How to Copy Build output to a Lab Environment Machine for TFS2013"
date: 2014-06-22 19:20:29 +0100
---

If you want to run Coded-UI test on Lab Environment machine then you need to copy the binaries files to that machine. You can create a script that does that, but you can also create some customization for the build process to do that as follows. In our scenario, we have two machines, the first one (**Visual Studio 2013 ALM RTM**) is a **TFS** machine with [**Test Control**](http://msdn.microsoft.com/en-us/library/hh546460.aspx "Setting Up Test Controllers in Lab Environments") and the second one (**Agent**) is a machine with **[Test Agent](http://msdn.microsoft.com/en-us/library/dd648127.aspx "Installing and Configuring Test Agents and Test Controllers")**.

![Machines](/assets/img/2014/06/machines.jpg)

The first step on the **Agent** machine is to share the folder that will hold the binaries.

![Sharing](/assets/img/2014/06/sharing.jpg)

From the **Tool Box**, type get and drag and drop [**GetBuildDetail**](http://msdn.microsoft.com/en-us/library/gg265783.aspx#Activity_GetBuildDetail "Get a reference to the IBuildDetail object (GetBuildDetail activity)") Activity. You need to put it between **Update Build Number** and **Run on Agent**. Click on variables and declare a new variable of type [**IBuildDetail**](http://msdn.microsoft.com/en-us/library/microsoft.teamfoundation.build.client.ibuilddetail.aspx "IBuildDetail Interface") to hold the return value from **GetBuildDetail** Activity. In my case, I called that variable **RadwanBuildDetail**.

![IBuildDetail-GetBuildDetail](/assets/img/2014/06/ibuilddetail-getbuilddetail1.jpg)

From the properties of the **GetBuildDetail** Activity, assign the result to the variable that we just declared.

![Assign BuildDetail variable](/assets/img/2014/06/assign-builddetail-variable.jpg)

From the Tool Box, drag and drop [**CopyDirectory**](http://msdn.microsoft.com/en-us/library/gg265783.aspx#Activity_CopyDirectory "Copy a directory (CopyDirectory activity)"). You must put it in **Run on Agent**. From the properties, select the source which is our variable and in the **Destination**, type the UNC path for our shared folder. Of course, in a real scenario, you will not hardcode that **Destination**; you will make that an argument, so you can enter that by just editing the **Build Definition**.

![CopyDirectory Activity](/assets/img/2014/06/copydirectory-activity.jpg)

If you run this build, the output of the drop folder will be copied to the Lab Management machine. [More information and tutorial about customizing build process](https://mohamedradwan-devops.github.io/posts/3-activities-part-1/ "Tutorial about customizing build process").
