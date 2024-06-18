---
layout: post
title: "Lab Management overview"
date:   2011-06-11 18:40:07 +0100
---

[Updated on April 17, 2012] You can see the full video series (93 videos) of install and configure TFS 2010 in enterprise, see the guide on the Codeplex <http://tfs10enterprise.codeplex.com/> [End of April 17, 2012 update]

### What is Lab Management?

Lab Management is a new tool in ALM 2010 that provides you with the ability to:

- **Manage Physical or virtual environments for your test team or QA:**

  As a tester, you have a group of physical or virtual machines that you will use to run your tests. Managing these machines through remote desktop or physical management can be very hard, but with Lab Management, life is easier.

- **Prepare a complex test environment in a few minutes with everything configured:**

  You can create a complex virtual environment in a few minutes. For example, you can create 5 machines, 3 of them running Windows 2008 R2, one running Windows 7 Ultimate, and the other running Windows Vista. You create all these machines from templates or virtual machines stored in the library on the SCVMM (System Center Virtual Machine Manager) in just a few minutes.

- **Run manual or automated tests on these environments and collect valuable info when bugs happen:**

  When you run an automated test or even a manual test, you need to collect important data like capturing the screen error, recording the error video, or even collecting the Event log info and many other important info from the machine that hosts the bug.

- **Collecting valuable info:**

  You will not only collect screen captures, video captures, or event logs. You can capture the whole environment (snapshot with Hyper-V) and it will be attached automatically to the test result. This way, the developer can open this snapshot and work on the machine that hosts the bug (No more "it\'s working on my machine").

There are many other things we will talk about throughout the series.
