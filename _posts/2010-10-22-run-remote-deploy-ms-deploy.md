---
layout: post
title:  "How to run remote deploy with MS Deploy?"
date:   2010-10-22 07:40:05 +0100
---

First of all you have to know that in order to install any web application using MS Deploy you mostly need MS Deploy to be installed on the destination machine, so go to the following page and download the MS Deploy [click here](http://technet.microsoft.com/tr-tr/library/dd569059%28WS.10%29.aspx), install it on the destination machine. If the destination will be a remote server, you only need to install the remote service on the remote server. In this case,you will use Msdeploy.exe from the local destination computer. The remote service is not required on both machines in such a scenario. For maximum flexibility in synchronization operations, you can install the remote agent service on both the source and destination computers, and verify that the service is started on both computers. By default the  service is not start so go to the service and start it.

[![Start Service](http://achocq.bay.livefilestore.com/y1phKr3acs-GA3JjswoDxZIfBipGF5FeovjHbXr3ndzGlef8Cm9XxE2NU5WB8F_czGKcO4lsQ0GM6pAwPRejWgYdkUIwE_saEFC/StartService.png?psid=1 "Serivce")]

In the local machine start build the application by command line or using the automated with the project properties.From the visual studio command line write the following 

```
MSbuild MyWebProject.csproj /T:Package /P:Configuration=Debug;PackageLocation=\"D:buildfolderRadwan.zip\"

```
This will produce the following: 

![Web Package](http://achocq.bay.livefilestore.com/y1phKr3acs-GA2pbmS-MTzURxwP-LIxo5PpEgLLMwAVWWcSxeEcPNlpYC58HIYyEDtqp2WZDCuL_ahxbsdsr1LIc60WRLdsFtmD/WebPackage.png?psid=1)

Go the MS Deploy from the command line and write a command like the following command: 

```
C:Program FilesIISMicrosoft Web Deploy\>D:MVCBuildMvcTestBuildMvcTestBuild_201010108_PublishedWebsitesMvcTestBuild_PackageMvcTestBuild.deploy.cmd
/T /M:MyServer /u:ServerUserName /p:ServerPassword

```

[![Deploy with what if](http://achocq.bay.livefilestore.com/y1phH12_t30I5fBGxHhTxk3hb40exuLXqSIFCcGrOyCpuEtiDkPosENeXtiq6fm9dka5I7L0ooCmAQHzrvaCIXigzeLpUH0522x/What%20if.png?psid=1)

Remember that the \" [T ]\" meaning \"what if\" which means test what will happen but not actually deploy.  This will
help you to fix any existing issues, if you find everything is OK you can change the [T ] to [Y,
] so you deploy it actually When you open your destination server you will find that your web application was deployed.

Have fun:-)