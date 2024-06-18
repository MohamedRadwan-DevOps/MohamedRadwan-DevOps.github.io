---
layout: post
title:  "Why and How to use IBuildDetails and BuildDefinition?"
date:   2010-10-10 07:40:05 +0100
---

Hi, In this episode I will talk about why and how to use IBuildDetails and buildDefinition object to get valuable information thought the build, this very important because IBuildDetails give you all information you need to know about the running build. You can go to my episode 1 and download the process that I will use [click-here](https://mohamedradwan-devops.github.io/2010/10/21/1-hello-world-of-team-build-2010/ "Episode 1")

#### Part 1 BuildNumber

* First you will create a clean Template and start following the image with order number, this will get the buildDetails object and assign it to my variable so you can use it throughout the build process

[![FirstStep](/assets/images/2010/10/FirstStep.jpg)](/assets/images/2010/10/FirstStep.jpg) You can download my process template from the episode 1 as I mention before

*   Right click on WriteBuildMessage task and choose properties and change _BuildMessageImportance_._High_ and give the message BuildDetail.BuildNumber

[![fourth](/assets/images/2010/10/fourth.jpg)](/assets/images/2010/10/fourth.jpg) Just queue a new build and open click on view log and you will see it log your build number 

[![Result2](/assets/images/2010/10/Result2.jpg)](/assets/images/2010/10/Result2.jpg)

#### Part 2 BuildDefinition

How to get information from the buildDefinition

*   When you create a new build definition you set the drop location
  
  [![DropLocation1](/assets/images/2010/10/DropLocation1.png)](/assets/images/2010/10/DropLocation1.png)

*   Now you can message the drop location as the following
  
  [![DropLocation2](/assets/images/2010/10/DropLocation2.jpg)](/assets/images/2010/10/DropLocation2.jpg)

*   Build and click on view log
  
  [![DropLocation3](/assets/images/2010/10/DropLocation3.jpg)](/assets/images/2010/10/DropLocation3.jpg)

*   You can also use the full path as the following
  
  [![fullPath0](/assets/images/2010/10/fullPath0.jpg)](/assets/images/2010/10/fullPath0.jpg)

*   Build and see view log

[![fullPath1](/assets/images/2010/10/fullPath1.jpg)](/assets/images/2010/10/fullPath1.jpg)

*   You can see what the build definition hold

[![ConcatenateString](/assets/images/2010/10/ConcatenateString.jpg)](/assets/images/2010/10/ConcatenateString.jpg) 

That's it