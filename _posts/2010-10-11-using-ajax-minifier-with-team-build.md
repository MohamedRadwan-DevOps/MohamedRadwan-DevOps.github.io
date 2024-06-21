---
layout: post
title:  "Using Microsoft Ajax Minifier with team build"
date:   2010-10-11 07:40:05 +0100
---

2 weeks ago I had a problem with Microsoft Ajax Minifier on Team Build 010 because my file doesn\'t\' minify, and I post 3 posts title \" Why Microsoft Ajax Minifier dosen\'t minfi the file when used with team build 2010? \" in ASP.NET, MSDN forum and Stackoverflow but with no result, the post has many views on both ASP.NET and MSDN forum but with
no answer except very kind person \"Sid Forcier\" that try to help me but also with no result. Part of the log file as the following:

```
Using \"AjaxMin\" task from assembly \"C:Program
FilesMSBuildMicrosoftMicrosoftAjaxajaxmintask.dll\". Task \"AjaxMin\"
Done executing task \"AjaxMin\". Done building target \"AfterBuild\" in
project \"MVCWithAjax.csproj\".

```
And after hard investigation I found the solution, the problem was that when I set the build definition I make the drop folder inside the D: drive  and the Team build copy the source code to the C:build\...., so the AjaxMin can\'t find any CSS or js in the whole D: drive, only dlls. And because the AjaxMin use search criteria to find the files and if it didn\'t find just doesn\'t do anything so it doesn\'t give me any error in the log file as you can see, so all I had to do just change the path to the CSS and JS to my source folder on the Team Build server as the
following:

[![Using AjaxMinifier](/assets/img/2010/10/AjaxMini.png)](/assets/img/2010/10/AjaxMini.png)

Remember how to use the partial path, its very important to know how to include a file and what is the wild card that you can use to refer to the path you want, here you can find good link to the MSDN that describe this point,
[click-here](http://msdn.microsoft.com/en-us/library/ms171453.aspx "Use Wildcard with files")
