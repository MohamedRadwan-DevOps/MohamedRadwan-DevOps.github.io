---
layout: post
title: "2-Why and How to use IBuildDetailes and BuildDefinition?"
date:   2010-10-23 12:57:13 +0100
---

Hi, In this episode I will talk about why and how to use IBuildDetailes
and buildDefination object to get valuable information throught the
build, this very important because IBuildDetailes give you all
information you need to know about the running build. You can go to my
episode 1 and download the process that I will use
[click-here](https://mohamedradwan-devops.github.io/posts/team-build-2010/ "Episode 1")

#### Part 1 BuildNumber

-   First you will create a clean Teamplate and start following the
    image with order number, this will get the buildDetails object and
    assign it to my variable so you can use it throughout the build
    process

[![FirstStep](/assets/img/2010/10/FirstStep.jpg)](/assets/img/2010/10/FirstStep.jpg)

You can download my process template from the episode 1 as I mention
before

-   Right click on WriteBuildMessage task and choose properties and
    change *BuildMessageImportance*.*High* and give the message
    BuildDetail.BuildNumber

[![fourth](/assets/img/2010/10/fourth-1024x526.png)](/assets/img/2010/10/fourth.jpg)

Just queue a new build and open click on view log and you will see it log your build number

[![Result2](/assets/img/2010/10/Result2.jpg)](/assets/img/2010/10/Result2.jpg)

#### Part 2 BuildDefinition

How to get infromation from the buildDefinition

-   When you create a new build definition you set the droplocation

[![DropLocation1](/assets/img/2010/10/DropLocation1.png)](/assets/img/2010/10/DropLocation1.png)

<!-- -->

-   Now you can message the drop location as thefollowing

[![DropLocation2](/assets/img/2010/10/DropLocation2-1024x463.png)](/assets/img/2010/10/DropLocation2.jpg)

<!-- -->

-   Build and click on view

    log[![DropLocation3](/assets/img/2010/10/DropLocation3.jpg)](/assets/img/2010/10/DropLocation3.jpg)

<!-- -->

-   You can also use the full path as the following
[![fullPath0](/assets/img/2010/10/fullPath0-1024x476.png)](/assets/img/2010/10/fullPath0.jpg)

<!-- -->

-   Build and see view log

[![fullPath1](/assets/img/2010/10/fullPath1.jpg)](/assets/img/2010/10/fullPath1.jpg)

-   You can see what the build definition hold

[![ConcatenateString](/assets/img/2010/10/ConcatenateString-1024x583.png)](/assets/img/2010/10/ConcatenateString.jpg)

That\'s it

