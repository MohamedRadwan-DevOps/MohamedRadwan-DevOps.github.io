---
layout: post
title: "Create One Main Build Process to Invoke Other Builds"
date: 2015-08-21 08:42:35 +0100
---

Contents 
- [Introduction](#Intro)
- [1: Build Definition](#Step1)
- [2: Loop Additions](#Step2)
- [3: Build Sequence](#Step3)
- [4: Running the Build with No Dependencies](#Step4)
- [Download the Process Template](#Download)

## Introduction {#Intro}

The main question is how to start a **build** when another build succeeds in [Team Foundation Server (TFS)](https://www.visualstudio.com/en-us/products/tfs-overview-vs.aspx)? In other words, how to invoke a [TFS Build](https://www.visualstudio.com/en-us/docs/build/define/build) from another TFS Build? For related information on working with **TFS**, you can also read about [Versioning Assembly with TFS Build 2013](https://mohamedradwan.com/posts/versioning-assembly-during-tfs-build-2013/) and [Creating and Deploying Web Package during TFS Build 2013](https://mohamedradwan.com/posts/creating-and-deploying-web-package-during-tfs-build-2013/), along with [Creating a TFS Build Custom Activity to Read XML Files](https://mohamedradwan.com/posts/create-a-tfs-build-custom-activity-to-read-from-file/) or [Rolling back DB and Web Applications during TFS Builds](https://mohamedradwan.com/posts/backup-and-restore-rollback-db-and-web-application-during-tfs-build/). 
A third-party library isn't needed to do so, all I had to do is to edit the default Lab Management process template which has already done that (invoked a build from other build).

>If you would like to learn more about using the [Build Variables](https://docs.microsoft.com/en-us/vsts/build-release/concepts/definitions/build/variables?tabs=batch) in [VSTS](https://www.visualstudio.com/team-services/) and Release Management, have a look at the following post: [VSTS Build variables and Echo](https://mohamedradwan.com/posts/vsts-build-variables-and-echo/). The post describes how to see the output at any point of time, while automating a process, through setting variables and displaying them during the build.
{: .prompt-tip }

I copied the build process and removed most of the [activities](https://msdn.microsoft.com/en-us/library/gg265783(v=vs.110).aspx), [variables](https://www.visualstudio.com/en-us/docs/build/define/variables), and arguments and did some modifications; the following is an image of all the processes, and I will explain what happens in each section:

[![1- Master TFS Build Process](/assets/images/2015/08/master-build-run-other-builds-all-the-process.jpg "1- Master TFS Build Process")](/assets/images/2015/08/master-build-run-other-builds-all-the-process.jpg)

You can see **[this video](https://www.youtube.com/watch?v=vev3Czaa1pA)**, if you would like to find more information about a walkthrough introducing the Release Management and Build Automation using TFS 2017/2015. Step by step about all process, starting from creating the project, check in the code in the source control, create a build definition and trigger the build, and also create a release pipeline. Learn how to configure properly the build steps, including Copy Files and Publish Build Artifacts. See how to create new release definition, add environments and link to build definition. Afterwards see how to add tasks to the release definition, like Windows Machine File Copy and configure it properly.

### Step 1: Build Definition {#Step1}

Here is the [Build definition](https://www.visualstudio.com/en-us/docs/build/define/create) that uses the process; it only has 4 arguments, and we can see that the **build definition arguments** are a list of **strings** so we can point to many builds as needed. Also, we have the option to run builds in sequence if builds depend on each other, or disable in the case of no dependencies. 

[![2- Master TFS Build Process: Build Definition](/assets/images/2015/08/master-build-run-other-builds-build-definition.png "2- Master TFS Build Process: Build Definition")](/assets/images/2015/08/master-build-run-other-builds-build-definition.png)

### More Info {#info}

Read about basic guidelines that you need to consider when building a **product backlog** in the following post, [Requirements (Epic, Feature, User Story), Task Size and Estimation in Agile and Scrum](https://mohamedradwan.com/posts/requirements-epic-feature-user-story-task-size-and-estimation-in-agile-and-scrum/), and also about its maintaining and refinement of product backlog in [Key tips for Maintaining good product backlog in Agile and Scrum](https://mohamedradwan.com/posts/key-tips-for-maintaining-good-product-backlog-in-agile-and-scrum/).

### Step 2: Loop Additions {#Step2}

In the following section, I just added a **loop** for each that iterates over the list of given builds and invokes each one. Note here that I check if we want to run the build in sequence, see the next step.

[![3- Master TFS Build Process: Looped Build Invocation](/assets/images/2015/08/run-other-workflow-tfsbuild-for-each-build-definitions.png "3- Master TFS Build Process: Looped Build Invocation")](/assets/images/2015/08/run-other-workflow-tfsbuild-for-each-build-definitions.png)

### You can see **[this video](https://www.youtube.com/watch?v=tfWCYXxeTmc)**

If you would like to find more information about how to integrate automated UI tests with Visual Studio build automation in order to be able to integrate with Continuous Integration & Continuous Delivery Pipeline. First, you need to add test category and rebuild the application. Note that the build should be configured as a process, not as a service in order to be able to run the automation UI.

Afterwards I am going to commit EasyRepo UI Automation framework in Team Explorer - Changes in order to committed and synchronize the changes in my local EasyRepo on VSTS. See how to create new build definition using .NET Desktop template, remove unnecessary tasks as Publish symbols path, Copy Files to and Publish Artifact drop, but keep the Use NuGet, NuGet restore, Build solution, VsTest - testAssemblies tasks. How to set the correct Test filter criteria, and Test assemblies. Additionally learn how to use VSTest.Console.exe in order to run the automation form from command line and to debug the failing test.

### Step 3: Build Sequence {#Step3}

If we want to run the build in a sequence (the condition is true) to make each build depend on the previous build status, so that if one build fails then the main build will stop and fail. To do this, I wait until the build is finished and change the main build status (success or fail) and if it fails then the main build will stop and fail (**ThrowOnError**), if it succeeds, it goes to the next iteration in the loop (waits for the next build).

[![4- Master TFS Build Process: Build Sequence](/assets/images/2015/08/run-build-in-sequence-wait-for-build-and-set-build-status.png "4- Master TFS Build Process: Build Sequence")](/assets/images/2015/08/run-build-in-sequence-wait-for-build-and-set-build-status.png)

>If you would like to start using [Visual Studio](https://www.visualstudio.com/) for developing, read the details about its installation, launching and creating a new project in my post [Get Started Developing with Visual Studio](https://mohamedradwan.com/posts/get-started-developing-with-visual-studio-2015/). If you prefer to use Mac, see how it looks in [Visual Studio for Mac](https://mohamedradwan.com/posts/visual-studio-for-mac/) post.
{: .prompt-tip }

### Step 4: Running the Build with No Dependencies {#Step4}

If we don't want to run the build in sequence (condition is false), we just need to [trigger](https://www.visualstudio.com/en-us/docs/build/define/triggers) all builds with no dependencies; this means the main build always succeeds even if other child builds fail because it's not dependent on them. The main build may even finish while other builds are still running, so I made the main build wait for the last triggered build in the loop; but if the last build finishes before a previous one, the main build will finish before all of the builds are finished, so I changed (**ThrowOnError**) to be false so the main build will not fail if the last build fails.
 
[![5- Master TFS Build Process: Build with No Dependencies](/assets/images/2015/08/wait-for-the-last-build-and-success-the-build-whenever.png "5- Master TFS Build Process: Build with No Dependencies")](/assets/images/2015/08/wait-for-the-last-build-and-success-the-build-whenever.png)

### Download the Process Template {#Download}

[[Download the Process Template](https://onedrive.live.com/redir?resid=4BCAA16D27B46600%2162122)]

### You can see **[this video](https://www.youtube.com/watch?v=uGAcWLnSU0A)**

If you would like to find more information about how to get started with Release Management and its advantages. See how to create a build definition using CI/CD Tools for VSTS Extensions. (I will be using Package Extension and Publish Artifact tasks), and also using DevOps-VSTS-POC trigger in order to enable CI. All of that in order to be able to publish, share, install and query versions.

You will see how to create release definition. Choose an artifact and configure source for the artifact and default version. See how to create different environments or clone the existing one. In my case I am going to create QA, Preproduction and Production environment, each with one phrase and one task. See also how to configure Publish Extension task for each environment. See an end-to-end continuous delivery pipeline using VSTS extension with Build and Release Management.
