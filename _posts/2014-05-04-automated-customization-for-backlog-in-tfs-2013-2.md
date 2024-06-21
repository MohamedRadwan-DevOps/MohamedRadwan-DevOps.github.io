---
layout: post
title: "Automated Customization for Backlog in TFS 2013"
date: 2014-05-04 14:06:59 +0100
---

In this blog post, I will share a PowerShell script that automates a comprehensive customization for **TFS 2013** Backlog. The script performs the following tasks:

- Export `Categories.xml`, `ProcessConfig.xml`, `Bug.xml` as `CustomBug.xml`, and `Feature.xml` as `Objective.xml`
- Rename the custom bug to be "Custom Bug" in `CustomBug.xml`
- Rename the Feature to be Objective in `Objective.xml`
- Change the Link Control option for the WI layout in `Objective.xml` to display Epic
- Edit the `Categories.xml` to change the Feature category to be Epic category
- Add the Custom Bug WI to the Requirement category
- Create a new custom category for the new Portfolio level
- Add the Object as the default work-item to this custom category
- Clone the Portfolio section in `ProcessConfig.xml`
- Change the new cloned portfolio to have the new custom category
- Rename the items in the second portfolio from Feature to be Epic
- Add a new color section for the new WI Epic and renamed the Feature to be Objective
- Add AssignTo column

All you need to do is create a new project, rename the project variable in the PowerShell script, and run it.

![PowerShell for Backlog TFS 2013](/assets/img/2014/03/powershell-for-backlog-tfs-2013.png)

[To continue reading, visit the complete article on the](http://blogs.msdn.com/b/mvpawardprogram/archive/2014/04/21/automating-visual-studio-team-foundation-server-tfs-2013-backlog.aspx "The Microsoft MVP Award Program Blog") [MVP blog website](http://blogs.msdn.com/b/mvpawardprogram/archive/2014/04/21/automating-visual-studio-team-foundation-server-tfs-2013-backlog.aspx).

[http://blogs.msdn.com/b/mvpawardprogram/archive/2014/04/21/automating-visual-studio-team-foundation-server-tfs-2013-backlog.aspx](http://blogs.msdn.com/b/mvpawardprogram/archive/2014/04/21/automating-visual-studio-team-foundation-server-tfs-2013-backlog.aspx)
