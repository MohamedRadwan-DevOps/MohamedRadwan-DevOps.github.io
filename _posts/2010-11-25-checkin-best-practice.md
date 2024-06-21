---
layout: post
title:  "Automate the best practice for check-in, including Get latest, deploy DB, Run test, check-in"
date:   2010-11-25 07:40:05 +0100
---

To make sure that all my team members didn\'t make any mistake when they check-in their pending change, I decide to write a best practice document that tell them what they have to do when they check-in their code, but what about automation and the key concept [**Automate every repeated tasks**] so I decide to automate these best practices and write an article describe how to do that, and this post also will prove that anything you need can be [**automated**] So here the process that will be automated

-   Get the latest change from TFS
-   Build the solution including all projects
-   Deploy the Main Database locally
-   Deploy the Test Database locally which hold the test data used in
    the data driven test
-   Run the sanity test or  BVT (Build Verification Test) which has
    belong to category 1 (Test the integration between DB and code)
-   Check-in the pending change

You can download the project from here [[**download**]](http://cid-4bcaa16d27b46600.office.live.com/self.aspx/Blog%20New%20Docs%20only/MS%20Build/Get%20latest%5EJDeploy%20DB%20and%20Run%20test%20using%20MSBuild/AutomateDatabaseAndTest.zip "Download the project")

I will create a new configuration called DebugForCheck-in, see the following 

[![Project File](/assets/img/2010/11/Project.png)](/assets/img/2010/11/Project.png)

You can also see the project configuration file as XML, see the following:

```xml

<Target Name="GetLatestFromTFS2010" AfterTargets="build">
    <Message Importance="high" Text="start GetLatest for the project" />
    <Exec Command='"C:Program Files (x86)Microsoft Visual Studio 10.0Common7IDETF.exe" get $/AutoDBand/AutomateDatabaseAndTest/AutomateDatabaseAndTest /recursive /login:YourUsername,YourPassword' ContinueOnError='false' />
</Target>

<!--===========Deploy Database============-->
<Target Name="DeployDatabase" AfterTargets="GetLatestFromTFS2010" Condition="'$(Configuration)' == 'DebugForCheck-in'">
    <Message Importance="high" Text="------------------ Deploying Database according to the connection string ------------------ " />
    <Message Importance="high" Text=" " />
    <MSBuild Projects="..DBDB.dbproj" Targets="Build;Deploy" />
</Target>

<!--============Run the Test==================-->
<Target Name="UnitTests" AfterTargets="DeployDatabase" Condition="'$(Configuration)' == 'DebugForCheck-in'">
    <Message Importance="high" Text="------------------ Running Unit Tests for category 1 only ------------------" />
    <Message Importance="high" Text=" " />
    <Exec Command='"C:Program Files (x86)Microsoft Visual Studio 10.0Common7IDEmstest.exe" /testcontainer:"..BLTestbinDebugBLTest.dll" /category:cat1' />
</Target>

<Target Name="Chekin-pendingChange" AfterTargets="UnitTests">
    <Message Importance="high" Text="------------------ start Check-in process ------------------" />
    <Message Importance="high" Text=" " />
    <Exec Command='"C:Program Files (x86)Microsoft Visual Studio 10.0Common7IDETF.exe" checkin $/AutoDBand/AutomateDatabaseAndTest/AutomateDatabaseAndTest /recursive /login:YourUsername,YourPassword' ContinueOnError='false' />
</Target>

```

That\'s it, have fun :-)

