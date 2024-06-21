---
layout: post
title:  "Code coverage with Team build and MVC or any web application"
date:   2017-08-01 07:40:05 +0100
---

- I just need to create a code coverage and display it with the team build but I face a problem when I follow the normal steps, so my question was why the code coverage doesn\'t appear with the team build? but there is no answer after little investigation here the result.
  
-  Fist the visual studio premium or Ultimate edition must be installed on the building machine so code coverage can viewed and calculated.

The MVC or the website needs additional test configuration and may normal configuration cause an error because I face the following error:

```
Test Run Error. Cannot initialize the ASP.NET project \'WebUIController\'. Exception was thrown: The web site could not be configured correctly; getting ASP.NET process information failed.

```
Requesting \'http://localhost:3352/VSEnterpriseHelper.axd\' returned an
error: 

```
The remote server returned an error: (500) Internal Server Error.

```
You can check here a bug that closed because it can\'t reproduced on Microsoft for this error
[Microsoft](https://connect.microsoft.com/VisualStudio/feedback/details/531946/test-run-and-team-build-fails-although-all-test-passed?wa=wsignin1.0 "The bug")
[Connect, click to see the bug](https://connect.microsoft.com/VisualStudio/feedback/details/531946/test-run-and-team-build-fails-although-all-test-passed?wa=wsignin1.0 "The bug")

-  So I read many articles but the most important one as the following,  it\'s very good but it\'s not cover all my cases.

[http://blogs.blackmarble.co.uk/blogs/rfennell/archive/2009/04/15/team-build-code-coverage-and-mvc.aspx](http://blogs.blackmarble.co.uk/blogs/rfennell/archive/2009/04/15/team-build-code-coverage-and-mvc.aspx "A good article")

So let\'s start

-   First you will see that you have 2 test configuration files by
    default (you can add more config file  if you want) when you create
    new test project in any solution so you can use one of them as a
    local configuration and the other with the team build if you want, 
    so every configuration has different values, remember the way that
    selecting the testing configuration is different, it depends on  the
    place you will build your solution on,  for example if you build
    your solution on your machine then you will select the desire test
    configuration from Visual  Studio menu Test\--\>Select Active test

<!-- -->

-   But if you build your solution on building machine using Team build
    so you will select this configuration from the build definition
    parameters window, when you create or edit build definition

[![Test Configuration in the solution](/assets/img/2017/08/Test-configuration-files.jpg)](/assets/img/2017/08/Test-configuration-files.jpg)

- Open the test configuration you want let\'s say its TraceAndTestImpact.testsettings, just double click on it and select code coverage and select the dll you want but remember don\'t select the web, you will configure it manually, and here is the tricky sometimes it\'s OK and sometimes it give me the previous error in the Microsoft connect, any way don\'t select it, save the file and close it.

[![Select code coverage](/assets/img/2017/08/Set-code-coverage.png)](/assets/img/2017/08/Set-code-coverage.png)

- Open the file again but this time with open with as XML and start adding new line to point to the Web dll as the class library but remember you have to set the absolute path because it\'s different on the source folder in the build machine,so you just need to go there and find where the path to the dll on the server machine and there.

[![Test Configuration in XMl](/assets/img/2017/08/Test-configuration-with-XML-viewer.png)](/assets/img/2017/08/Test-configuration-with-XML-viewer.png)


- Build your application on the build machine,  now you should see the code coverage for the class libraries and the MVC or the Web Application.
