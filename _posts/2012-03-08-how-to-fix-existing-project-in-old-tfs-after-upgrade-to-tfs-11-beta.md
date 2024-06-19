---
layout: post
title: "How to Fix Existing Projects in Old TFS After Upgrade to TFS 11 Beta"
date:   2012-03-08 21:48:29 +0100
---

[Updated on March 13, 2012]

[Very useful links]
[How to add new tabs like storyboard and other fixes](http://blogs.msdn.com/b/visualstudioalm/archive/2012/03/06/get-your-agile-project-fixed-after-an-upgrade-from-tfs2010-to-tfs11-beta.aspx?ocid=soc-n-eg-elite--MRadwan "Hofman, how to fix?")
[Upgrade project from Buck Hodges](http://blogs.msdn.com/b/buckh/archive/2012/03/05/updating-a-team-project-to-use-new-features-after-upgrading-to-tfs-11-beta.aspx?ocid=soc-n-eg-elite--MRadwan "Buck Hodges") 

When I completed upgrading my environment to [TFS 11 Beta](https://mohamedradwan.com/category/visual-studio-11-beta/ "Visual Studio 11 Beta"), ([Upgrade to TFS 11 Beta](https://mohamedradwan.com/posts/upgrade-tfs-2010-to-tfs-11-beta-step-by-step-and-its-prerequisites/ "Upgrade to TFS 11 Beta")), I found the following error in the Web Access:

> [TF400508: The current process settings are either missing or not valid. These settings must be defined by a project administrator]

As shown in the following images:

![3-7-2012 11-31-58 PM](/assets/images/2012/03/3-7-2012-11-31-58-PM.png)

![3-8-2012 10-31-52 PM](/assets/images/2012/03/3-8-2012-10-31-52-PM-1024x373.png)

This issue occurs because this page uses new work items that did not exist in the old project on the old TFS. If we create a new project, it's OK because we will use the new process, but for the existing project, we must update them manually. So we have to do the following:

- Download and extract the following zip file:

  [http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=29047](http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=29047 "Download it")

- Open Visual Studio 11 Beta command prompt and type the following command:

```bash
updateProject CollectionURL ProjectName TemplateName
```

See the following image 

[![3-8-2012 10-59-14 PM](/assets/images/2012/03/3-8-2012-10-59-14-PM-1024x562.png)](/assets/images/2012/03/3-8-2012-10-59-14-PM.png)

And this will import the new work items to my old project, remember that
if we do customizing on the process template we will not be able to
upgrade, If we have customized the type definitions provided with these
process templates, we may need to modify the definition files for
process configuration prior to import. In particular, if we have made
changes to the workflow for those types that track backlog items, bugs,
and tasks, we may need to modify the process configuration files prior
to importing them. For more information we can see the following link
[http://msdn.microsoft.com/en-us/library/ff432837(v=vs.110).aspx#download](http://msdn.microsoft.com/en-us/library/ff432837(v=vs.110).aspx#download "Link")
To download Visual Studio and TFS 11 Beta click on the following link
[http://www.microsoft.com/visualstudio/11/en-us/downloads](http://www.microsoft.com/visualstudio/11/en-us/downloads)

