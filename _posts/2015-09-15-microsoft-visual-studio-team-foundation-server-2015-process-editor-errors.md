---
layout: post
title: "Microsoft Visual Studio Team Foundation Server 2015 Process Editor errors"
date:   2015-09-15 13:50:02 +0100
---

As we know that **[Visual Studio 2015 and Team Foundation Server 2015](https://www.visualstudio.com/?Wt.mc_id=DX_MVP4039889)** has been released, when I started working with the new [TFS Power Tool](https://visualstudiogallery.msdn.microsoft.com/898a828a-af00-42c6-bbb2-530dc7b8f2e1), I found that there are some errors with the Process Editor tool. If we try to customize some types of the work-items, we might see the following error: 

`Control " references a non-existing field System.ID.`

![non-existing field System.ID](/assets/img/2015/09/non-existing-field-system-id.png)

[Tip]{.ion-tip} If you would like to learn more about different tools and ways for Team Foundation Server to Visual Studio Team Services migration, - have a look at the [quick guide about real stories for migrating Team Foundation Server to Visual Studio Team Services](https://mohamedradwan-devops.github.io/posts/published-a-quick-guide-about-real-stories-for-migrating-team-foundation-server-to-visual-studio-team-services/). The guide describes some of the real migration scenarios and explains how to use different tools for several cases.

We just need to change the name of the control to the right one with small letters as shown below:

![Work-Item System.id](/assets/img/2015/09/wrok-item-system-id.png)

You can see the following video, if you would like to find more information about a walkthrough introducing the Release Management and Build Automation using TFS 2017/2015. Step by step about all processes, starting from creating the project, check in the code in the source control, create a build definition and trigger the build, and also create a release pipeline. Learn how to properly configure the build steps, including Copy Files and Publish Build Artifacts. See how to create a new release definition, add environments, and link to build definition. Afterwards, see how to add tasks to the release definition, like Windows Machine File Copy and configure it properly.

{% include embed/youtube.html id='vev3Czaa1pA' %}

Another error: 

```
VS402479: You can't overwrite the Scrum process template, because it's locked. For more information about customizing process templates, click 'Help'
```

![VS402479 You can't overwrite the Scrum process template, because it's locked. For more information about customizing process templates, click Help.](/assets/img/2015/09/vs402479-you-cant-overwrite-the-scrum-process-template-because-its-locked-for-more-information-about-customizing-process-templates-click-help.png)

>The post [Upgrade to TFS 2018 Has Been Done in Production](https://mohamedradwan-devops.github.io/posts/upgrade-to-tfs-2018-has-been-done-in-production/) describes a full upgrade and migration from TFS2015 to TFS2018 and describes the improvements over the old TFS 2015.
{: .prompt-info }

We just need to generate a GUID and add it to the ProcessTemplate.xml file as shown below:

![GUID for TFS Process Template](/assets/img/2015/09/guid-for-tfs-process-template.png)

Another error is that the **Reason** field is read-only for the **Product Backlog Item**. So, no matter what you added as extra reasons, it wouldn't appear. To fix that, we just need to change that to false, as shown in the image below:

![ProductBacklogItem layout](/assets/img/2015/09/productbacklogitem-layout1.png)

You can see the following video, if you would like to find more information about how to get started with Release Management and its advantages. See how to create a build definition using CI/CD Tools for VSTS Extensions. (I will be using Package Extension and Publish Artifact tasks). Also, using DevOps-VSTS-POC trigger to enable CI. All of that to be able to publish, share, install, and query versions.

You will see how to create a release definition, choose an artifact and configure the source for the artifact and default version. See how to create different environments or clone the existing one; in my case, I am going to create QA, Preproduction, and Production environments, each with one phase and one task. See also how to configure the Publish Extension task for each environment. See an end-to-end continuous delivery pipeline using VSTS extension with Build and Release Management.

{% include embed/youtube.html id='uGAcWLnSU0A' %}