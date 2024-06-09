---
layout: post
title: "Estimating the time for migrating projects to VSO (Visual Studio Online)"
date: 2015-07-15 15:47:47 +0100
---

I wrote in a previous post about [how to migrate projects to VSO with different tools](https://mohamedradwan.com/posts/migration-to-vso-visual-studio-online-with-different-tools/), but the most important question was [what is the estimated time for each project???]. This was really a hard question to answer, so I created a [command line tool](https://visualstudiogallery.msdn.microsoft.com/f25cd380-7d2b-4aa1-b0d7-b10156702dc9) that helps in estimating the size of the project so we can estimate the time needed for migrating each project.

> If you would like to start using [Visual Studio](https://www.visualstudio.com/) for developing, read the details about its installation, launching, and creating a new project in my post [Get Started Developing with Visual Studio](https://mohamedradwan.com/posts/get-started-developing-with-visual-studio-2015/). If you prefer to use Mac, see how it looks in [Visual Studio for Mac](https://mohamedradwan.com/2017/07/30/visual-studio-for-mac/) post.
{: .prompt-info }

Here is the size for some projects and the actual time needed for migrating each one:
![TFSCount Report](/assets/images/2015/07/tfscount-report.png)

You can see the following video if you would like to find more information about my personal experience of migrating Team Foundation Server to Visual Studio Team Services using Database Import Service or TFS Migrator tool provided by Visual Studio Team. Going through all six phases of the migration, following the migration guide provided by Microsoft as a walkthrough. You will see how to get started with the migration process and which prerequisites should be completed. The most important prerequisite is that you must have Azure Active Directory to use the TFS Migrator tool. See more about the two different process models supported by VSTS, Inherited and Hosted XML. See which decisions you should make and how to validate them, for example, which customizations you should keep and which to remove. To prepare the first collection dacpac, first, you should prepare the Azure Storage Container, create the dacpac file, and upload it. To prepare the second collection Azure VM, you should install SQL Server, back up the DB from the collection, and upload it to the Azure storage container. See first how to import (dry-run) and how to change the configuration afterward to import (production).

{% include embed/youtube.html id='7C6LG6k4wcU' %}
