---
layout: post
title: "Do I need to remove Lab Management from a Collection when I Upgrade?"
date: 2014-03-13 20:29:25 +0100
---

This is really a very important question. The answer depends on some conditions. If you are upgrading to a different domain or if you will use a different SCVMM (System Center Virtual Machine Manager), you must delete the resources that are used by Lab Management from the collection database. This includes virtual machines, templates, team project host groups, and team project library shares. Otherwise, you will keep them. You will need to re-create the Lab Management assets after you finish the upgrade.

To remove the Lab Management resources, you will use:
```shell
TFSConfig Lab /Delete /External
```
The following is the notification when you don\'t delete them. 

**Note**: this also applyed for moving collection to another server 

>Team Foundation Server could not tear down
the deployment rig on environment in project. Delete the Visual Studio
2010 Team Foundation Build Agent associated with this environment
manually using Team Foundation Server Administrator Console. Exception
Details: TF30040: The database is not correctly configured. Contact your
Team Foundation Server administrator.

![Delete the Lab Management resources](/assets/img/2014/03/delete-the-lab-management-resources.jpg)

