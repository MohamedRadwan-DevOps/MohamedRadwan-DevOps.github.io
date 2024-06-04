---
layout: post
title:  "MVC2 MS Build error MSB4019"
date:   2010-05-30 07:40:05 +0100
---

When I prepar for my new MVC2 project that will use TFS and MS Build for
daily build, I decide to create Hello world with MVC2 that use MS Build
so I can know what the problems that I may face during my real project
and here are the problems and how I deal with it. This post will be
helpful of any errors of the following:

-   MVC2 error with MS Build
-   error MSB4019: The imported project \"C:Program
    FilesMSBuildMicrosoftVisualStudiov10.0WebApplicationsMicrosoft.WebApplication.targets\"
    was not found
-   The type or namespace name \'Mvc\' does not exist in the namespace
    \'System.Web\' (are you missing an assembly reference?

I use Get Check in Trigger for build so when I check in my code it
queue  my code for build and it has an error. 

Open the error and click on view log 

![Build Error Message](/assets/images/2010/06/ViewLogFile.jpg)

See where the pat that locate for the need files

![Log file](/assets/images/2010/06/LogFile.jpg)

Open this target in the MS Build machine, in my case will be as the following

![MS Build Machine path from Log file](/assets/images/2010/06/The-WebApplication-folder.jpg)

Open your Visual Studio 2010 machine Copy the WebApplications and put it in the same target in the MS Build machine as
the previous image

![File copied to MS Build machine](/assets/images/2010/06/MSBuildTargets-Files.jpg)

Queue another Build the error should disappear but an new error displayed, this error was that MVC dll can\'t be found So I open my Visual Studio machine and copy this dll 

![MVC dll](/assets/images/2010/06/MVCDll.jpg)

And put it in the following path, and to help another error I had to put it in the
GAC also C:Program FilesReference AssembliesMicrosoftFramework.NETFrameworkv4.0 And now the MVC 2 project get in the queue and build  successfully.
