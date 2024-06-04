---
layout: post
title:  "MSBuildExtensionPack how to?"
date:   2010-10-15 07:40:05 +0100
---

I am now interested of streamline the building and the deployment of the
application to the QA or the Production because this process take too
much time which are repetitive tasks that we should automate, so with
the TeamBuild 2010 this will be very productive direction. so I read
about MSBuildExtensionPack which is open source project exists on the
[codeplex](http://msbuildextensionpack.codeplex.com/) it has many tasks
that you can execute during or after your build this depend on the
target element you define, some of it\'s task for example:

-   System Items: Active Directory, Certificates, COM+, Console, Date
    and Time, Drives, Environment Variables, Event Logs, Files and
    Folders, FTP, GAC, Network, Performance Counters, Registry,
    Services, Sound
-   Code: Assemblies, CAB Files, Code Signing, DynamicExecute, File
    Detokenisation, GUID's, Mathematics, Strings, Threads, Xml, Zip
    Files
-   Applications: BizTalk 2006 / 2009, Email, IIS6, IIS7, MSBuild,
    SourceSafe, SQL Server 2005, SQL Server 2008, StyleCop, Twitter,
    Team Foundation Server, Visual Basic 6, Windows Virtual PC, WMI

It\'s has over 355 MSBuild Tasks So let\'s start making a sample
application from the beginning to the end that run an SQL script and
pop-up a window with message First install the package, it prefers to
use the default location or other wise you need to write the *(FQN)*
fully qualified name  to the library  it in your project file Read the
help and see the sample file in the installation folder you will find
example of most tasks you need Create your project that you want to use,
let\'s say it\'s console Application

-   Right click on the project and choose unload project
    
    ![How to unload project](/assets/images/2010/10/UnloadProject.jpg)

<!-- -->

-   Right click on the project and click edit 
  
    ![How to edit project file](/assets/images/2010/10/EditProject.jpg)

Minimum all the sub elements so you can see the whole file Start add the
following inside ItemGroup element
`<Files Include=\"C:SQLQuery1.sql\"/\>`

-   Import ExtensionPack tasks, if it in the default place you just
    write
    `<Import Project=\"\$(MSBuildExtensionsPath)ExtensionPack4.0MSBuild.ExtensionPack.tasks\"/\>`
    But if it\'s not in the default you have to import it with the full path
    `<Import Project=\"C:Program FilesMSBuildExtensionPack4.0MSBuild.ExtensionPack.tasks\"/\>`
    

<!-- -->

-   Write a target element or just uncomment the commented target
    \"before build or after build\"

<!-- -->

-   Put your task between the target and use the task parameters as in
    the help file and the example, it\'s better to review the help file
    because some parameters are required and some are optional, so the
    final project file will be like the following 
    
    ![Project file from inside](/assets/images/2010/10/csprojFile.jpg)

<!-- -->

-   Build the application, you should see pop-up window and your
    database will be affected.

<!-- -->

-   You can download the project from
    [here](http://cid-4bcaa16d27b46600.office.live.com/self.aspx/.Public/Blog%20New/MSBuild/MSBuildExtention/MSBuildExtenstionPack.zip "MSBuildExtentionExample")

Have fun :-)
