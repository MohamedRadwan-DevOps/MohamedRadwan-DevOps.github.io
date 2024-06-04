---
layout: post
title:  "Auto Deploy your Website for QA with Team Build"
date:   2010-10-15 07:40:05 +0100
---

I need to Deploy the website to the QA machine with team build so I search for how to do that and I found very good article of [Ewald Hofman](http://www.ewaldhofman.nl/post/2010/04/12/Auto-deployment-of-my-web-application-with-Team-Build-2010-to-add-Interactive-Testing.aspx "Edwld Hofman")

which describe how you auto deploy your website and it\'s very good post, but there  is 2 issues I faced when I implement this example.

First Issue: The Package folder that auto generated doesn\'t generated on the Team build, the reason was very easy, because I don\'t have Visual Studio installed on the Server machine, so by Installing the visual studio everything is now working and the generated package folder now
exist. 

Second Issue: How to deploy the project to another machine, so you have to write the post build as the following if

```
\"\$(ConfigurationName)\" == \"Test\"
\"\$(TargetDir)\_PublishedWebsitesMyProject_PackageMyProject.deploy.cmd\"
/Y /M:YourServerName/u:YourUserName /p:YourPassword 

```

For more information with how to make package and deploy it using MSDeploy [click-here](https://mohamedradwan.com/2010/10/10/how-to-run-remote-deploy-with-ms-deploy/ "Using MSDeploy")

> You have to see [Ewald Hofman](http://www.ewaldhofman.nl/post/2010/04/12/Auto-deployment-of-my-web-application-with-Team-Build-2010-to-add-Interactive-Testing.aspx "Example") post because my post depend on it, because I didn\'t want to repeat any examples.
{: .prompt-info }


