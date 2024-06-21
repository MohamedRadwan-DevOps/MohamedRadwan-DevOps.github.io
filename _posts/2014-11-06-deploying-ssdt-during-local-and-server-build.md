
---
layout: post
title: "Deploying SSDT During Local and Server Build"
date: 2014-11-06 15:05:05 +0100
---

Four years ago, I wrote a post about [how to deploy VS DB (Visual Studio Database Project) to your local SQL Server during your local build](https://mohamedradwan-devops.github.io/posts/automate-the-best-practice-for-check-in-including-get-latest-deploy-db-run-test-check-in/ "NOVEMBER 13, 2010 BY MOHAMED RADWAN (MVP) Automate the best practice for check-in, including Get latest, deploy DB, Run test, check-in").

As you may already know, a new version of [SSDT (SQL Server Data Tool)](http://msdn.microsoft.com/da-dk/data/tools.aspx "Sql Server Data Tool") has been released with VS 2012 to replace the normal VS DB project that was existing with VS 2010, and of course the deployment changed. For more information and understanding about SSDT, see this post: [What\'s New in TFS 2012?- SSDT (SQL Server Data Tool)](https://mohamedradwan-devops.github.io/posts/whats-new-in-tfs-2012-ssdt-sql-server-developer-tool/ "What's New in TFS 2012?- SSDT (SQL Server Data Tool)").

Now we have a feature called publish profile, which you can put all your settings in that file and use it afterwards to deploy the DB. This post has two sections:

- Deploy and publish SSDT to local SQL Server during local build
- Deploy and publish SSDT to a shared SQL Server during TFS Build

## Deploy and publish SSDT to local SQL Server during local build

If you need to work with SSDT for SQL Server 2014, then you will need to install the latest SSDT. It\'s not included in VS update 3. [Download SSDT](http://blogs.msdn.com/b/ssdt/archive/2014/07/24/creating-an-administrative-install-of-ssdt-update-for-visual-studio-2013.aspx).

![SSDT for SQL Server 2014](/assets/img/2014/11/ssdt-for-sql-server-2014.jpg)

**1. Using [SqlPublishTask](http://msdn.microsoft.com/en-us/library/microsoft.data.tools.schema.tasks.sql.sqlpublishtask(v=vs.103).aspx) of MSBuild**  
I edit the SSDT project file as the following:

![local publish SSDT](/assets/img/2014/11/local-publish-ssdt.png)


```xml
<Target Name="DeployDB" AfterTargets="build" Condition="'$(Configuration)' == 'Local'">
    <Message Importance="high" Text="************ Start Deploying DB ************" />
    <Message Importance="high" Text="Deploying Project: $(MSBuildProjectDirectory)$(MSBuildProjectName).sqlproj" />
    <Message Importance="high" Text="Deployment Profile: $(MSBuildProjectDirectory)PublishProfiles$(MSBuildProjectName).local.publish.xml" />
    <MSBuild 
        Projects="$(MSBuildProjectDirectory)$(MSBuildProjectName).sqlproj" 
        Properties="SqlPublishProfilePath=$(MSBuildProjectDirectory)PublishProfiles$(MSBuildProjectName).local.publish.xml" 
        Targets="sqlPublish" />
</Target>
```

I used some of [MSBuild Reserved and Well-Known Properties](http://msdn.microsoft.com/en-us/library/ms164309.aspx) like
`\$(MSBuildProjectName) and \$(MSBuildProjectDirectory)`, for complete
list, [click on this link](http://msdn.microsoft.com/en-us/library/ms164309.aspx)


2.Using MS Build Command line with [SqlPublishTask](http://msdn.microsoft.com/en-us/library/microsoft.data.tools.schema.tasks.sql.sqlpublishtask(v=vs.103).aspx)

[![MSBuild SqlPublishTask command line](/assets/img/2014/11/msbuild-sqlpublishtask-command-line.png)](/assets/img/2014/11/msbuild-sqlpublishtask-command-line.png)

```xml
msbuild /t:build;publish "C:\TFS\Source\Model\Calculator\Calculator.DB\Calculator.DB.sqlproj" /p:SqlPublishProfilePath="C:\TFS\Source\Model\Calculator\Calculator.DB\PublishProfiles\Calculator.DB.local.publish.xml"

"%MSBuildProgramFiles32%\MSBuild\12.0\Bin\msbuild" /t:build;publish "C:\TFS\Source\Model\Calculator\Calculator.DB\Calculator.DB.sqlproj" /p:SqlPublishProfilePath="C:\TFS\Source\Model\Calculator\Calculator.DB\PublishProfiles\Calculator.DB.local.publish.xml"

```

-   If we run the MS Build from withing the project path we can use
    relative paths instead of absolute paths
-   To use MSBuild without path, we need to open Visual Studio command
    line otherwise we may having this error
    
    >exited with code 9009
    {: .prompt-danger} 
    which means it couldn\'t find the MSBuild.exe\", so I will need to use the full path and this is
    always the case when working with pre and post build events

3.Using [SqlPackage.exe](http://msdn.microsoft.com/en-us/library/hh550080%28v=VS.103%29.aspx)

SqlPackage.exe is a command line utility that automate some of the DB
development tasks We can call SqlPackage as a post build event for SSDT
project as the following: 

```xml
"$(MSBuildProgramFiles32)\Microsoft SQL Server\110\DAC\bin\sqlpackage" /a:publish /sf:"$(SolutionDir)$(ProjectName)$(OutputPath)Calculator.DB.dacpac" /pr:"$(SolutionDir)$(ProjectName)Calculator.DB.local.publish.xml"

```

The .dacpac file is the output of building sqlproject, as the dll is the output of building a class library

## Deploy and publish SSDT to a shared SQL Server during TFS Build

There are many ways too, the SSDT\'s team blog create a great post for
all ways, for more info, click on the following link: [SQL Server Database Projects and Team Foundation Build](http://blogs.msdn.com/b/ssdt/archive/2014/07/24/sql-server-database-projects-and-team-foundation-build.aspx#publishDb "SQL Server Database Projects and Team Foundation Build")

1.Using [SqlPublishTask](http://msdn.microsoft.com/en-us/library/microsoft.data.tools.schema.tasks.sql.sqlpublishtask(v=vs.103).aspx)
of MSBuild I will send some MDBuild arguments in the build
definition as the following:

[![TFSBuild-SSDT1](/assets/img/2014/11/tfsbuild-ssdt1.png)](/assets/img/2014/11/tfsbuild-ssdt1.png)


```xml
/t:Build;Publish /p:SqlPublishProfilePath=../Calculator.DB\PublishProfiles\Calculator.DB.local.publish.xml
```

But because my solution has many projects, not only the SSDT project, I build the solution file, not just the SSDT project file. This means the build argument will be sent to each project file in the solution, which gives an error with one of the Win Form projects, as shown below:

>MSBuild error MSB3021: Unable to copy file
C:Program Files (x86)MSBuild12.0binamd64Microsoft.Common.CurrentVersion.targets (4691): Could not copy the file "exe.manifest" because it was not found.
{: .prompt-danger }

This error will disappear if we only build SSDT. Of course, I can use other ways like using SqlPackage.exe with a custom build, but since this is the way I did on my local build, I preferred to do the same on the build server. So, I customized the build as shown below:

[![SSDT with TFSBuild](/assets/img/2014/11/ssdt-with-tfsbuild.png)](/assets/img/2014/11/ssdt-with-tfsbuild.png)

I used 2 editors:

- Microsoft.TeamFoundation.Build.Controls.BuildProjectListEditor
- Microsoft.TeamFoundation.Build.Controls.StringListEditor

These allow me to select multiple build projects and multiple publish profiles. For more information about Build Editors, see the following post: [TFS Build Editors and Build Process Metadata](https://mohamedradwan-devops.github.io/posts/tfs-build-editors-and-build-process-metadata/ "TFS Build Editors and Build Process Metadata").

To customize the process, I added 2 arguments and added them to the metadata to categorize them under the SSDT section in the Build definition:

[![SSDT Section](/assets/img/2015/01/ssdt-section.png)](/assets/img/2015/01/ssdt-section.png)

I used the MSBuild activity to run MSBuild for the SSDT projects that are selected by the build definition:

[![Run MSBuild for SSDT](/assets/img/2015/01/run-msbuild-for-ssdt.png)](/assets/img/2015/01/run-msbuild-for-ssdt.png)

You can download the process template by clicking on the following link: [TFS Process Template](https://onedrive.live.com/redir?resid=4BCAA16D27B46600%2122421 "Download process template")

