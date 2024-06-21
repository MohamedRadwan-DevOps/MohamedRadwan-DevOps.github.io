---
layout: post
title: "Quick overview about how and why to use NLog"
date:   2014-09-15 08:31:28 +0100
---

I needed to use a Logging Framework, every time using logging frameworks, it ends up with wasting some hours because the configuration makes me feel it's better to create my own :-). I already started to create a small one but I found this is exactly reinventing the wheel, so I decided to give some time for different logging frameworks' configurations.

**Log4Net**, I used that one because I found it has been used for some projects we have. It took all day for fixing up some configuration errors that I found, at the end they were bugs, and I needed to make some workarounds to fix them. I don't recommend anyone to use this framework as it has not been updated for a long time (2006).

**NLog**, it was very simple, very nice... I decided to summarize my overview about it:

Here are the steps to use NLog:

- Add reference to NLog framework using NUget (**PM> Install-Package NLog**)
- Add config file using NUget (**PM> Install-Package NLog.Config**)
- Add at least one target in the **Target** section in the config file
- Add at least one rule in the **Rules** section that uses any target from the **Target** section
- Create an instance of the Logger class inside the class you want to use NLog 

  ```csharp
  private static readonly Logger Logger = LogManager.GetCurrentClassLogger();
  ```

-   Call any method of Logger object (Log, Trace, Debug, etc..)

**Notes**:

-   [NLog tutorial](https://github.com/NLog/NLog/wiki/Tutorial "NLog tutorial")
-   [All Target types](https://github.com/NLog/NLog/wiki/Targets)
-   [All Layouts Renders](https://github.com/NLog/NLog/wiki/Layout-renderers)
-   we can make combinations for target and rules for e.x,
    -   We can use one target for each rule Error in Event Log,
        Info in a File
    -   We can use multiple rules for the same target Error and
        Info in the same File
    -   We can use multiple targets for the same rule Error and
        Info in both Event Log and in the same File or even in many
        Files

Here is the config file with some notes and description of some elements and attributes

```xml
<?xml version="1.0" encoding="utf-8" ?>
<nlog xmlns="http://www.nlog-project.org/schemas/NLog.xsd"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <!-- See https://github.com/nlog/nlog/wiki/Configuration-file for information on customizing logging rules and outputs. -->
  <targets>
    <target name="logfile" xsi:type="File" fileName="file.txt" />
    <target name="console" xsi:type="Console" />
    <target name="errors" xsi:type="File" fileName="ErrorLog.txt" layout="Caller: ${callsite:className=true:fileName=true:includeSourcePath=true:methodName=true} ${newline} LogDirectory: ${nlogdir} ${newline} Process: ${processname} ${newline} ${longdate} ${message} ${exception:format=tostring} " />
    <!-- add your targets here -->
    <!-- <target xsi:type="File" name="f" fileName="${basedir}/logs/${shortdate}.log" layout="${longdate} ${uppercase:${level}} ${message}" /> -->
  </targets>
  <rules>
    <logger name="*" minlevel="Trace" writeTo="logfile" />
    <logger name="*" minlevel="Trace" writeTo="errors" />
    <logger name="*" minlevel="Info" writeTo="console" />
    <!-- add your logging rules here -->
    <!-- <logger name="*" minlevel="Trace" writeTo="f" /> -->
  </rules>
</nlog>
```
