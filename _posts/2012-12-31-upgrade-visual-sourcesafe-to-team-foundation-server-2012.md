---
layout: post
title: "Upgrade Visual Sourcesafe to Team Foundation Server 2012"
date: 2012-12-31 11:36:06 +0100
---

In this post I will explain how to upgrade and migrate projects or repositories from [VSS or Visual SourceSafe 2005](http://msdn.microsoft.com/en-us/library/3h0544kx(v=vs.80).aspx "Visual SourceSafe"){target="_blank"} to [TFS or Team Foundation Server 2012](http://msdn.microsoft.com/en-us/vstudio/ff637362.aspx " TFS or Team Foundation Server 2012"){target="_blank"}.

![1-Upgrade VSS Projects to TFS 2012 intro](/assets/images/2012/12/1-upgrade-vss-projects-to-tfs-2012-intro.jpg)

A step by step video for the post:

{% include embed/youtube.html id='XZrHYsVadao' %}

1. **Open Visual SourceSafe Administration.**

![2-Open VSS Administration](/assets/images/2012/12/2-open-vss-administration.jpg)

2. **Create new Database or Repository for VSS Projects.**

![3-Create new DB](/assets/images/2012/12/3-create-new-db.jpg)

3. Click **Next** and select the location of the Database. I create a folder called **Marvel-VSS**.

![4-Select location of DB](/assets/images/2012/12/4-select-location-of-db.jpg)

4. **Create a project inside that Repository.** Its name will be **MVCProject**.

![5-Add Project](/assets/images/2012/12/5-add-project.jpg)

5. **Create a mapping folder on the local HDD.** Its name will be **My Work**.

![6-Set working folder in VSS](/assets/images/2012/12/6-set-working-folder-in-vss.jpg)

6. **Navigate to the folder using Windows Explorer and add a new text file** as an example of the source code of your project. I typed "Hello World!" inside the file.

![7-Add file to the project](/assets/images/2012/12/7-add-file-to-the-project.jpg)

7. **Add the existing source code (text file) to the VSS Repository.**

![8-Add file to VSS](/assets/images/2012/12/8-add-file-to-vss.jpg)
8. **Check-in files into the VSS.**

![9-Check-in files](/assets/images/2012/12/9-check-in-files.jpg)

9. **Navigate to the second machine that has TFS 2012 and create a new project.** Its name will be **Marvel-TFS**.

![10-Create new Team Project](/assets/images/2012/12/10-create-new-team-project.jpg)

10. **Download the [Visual Source Safe Upgrade Tool](http://visualstudiogallery.msdn.microsoft.com/867f310a-db30-4228-bbad-7b9af0089282 "Visual Source Safe Upgrade Tool")**

![11-Visual-SourceSafe Upgrade tool](/assets/images/2012/12/11-visual-sourcesafe-upgrade-tool.jpg)

11. **Install the upgrade tool.**

![12-setup upgrade tool](/assets/images/2012/12/12-setup-upgrade-tool.jpg)

12. **Launch VSS Upgrade Tool Wizard and browse to the Marvel-VSS Repository on the VSS machine.** Click on **List Available Projects** to retrieve the project from that Repository, click on the check-box and then click **Next**.

![13-VSS Upgrade wizard](/assets/images/2012/12/13-vss-upgrade-wizard.jpg)

13. **Browse to the created project on TFS (Marvel-TFS) and select it.**

![14-Choose team project to migrate on](/assets/images/2012/12/14-choose-team-project-to-migrate-on-1.jpg)
14. **Click Next and then click on Verify.** After that click on **Upgrade.**

![15-Readness Checks](/assets/images/2012/12/15-readness-checks-1.jpg)

15. **Review the completion of the upgrade.**

![16-Success](/assets/images/2012/12/16-success-1.jpg)

16. **Review the team project on TFS to make sure that the source code has been migrated successfully.**

![17-examin the file on the TFS](/assets/images/2012/12/17-examin-the-file-on-the-tfs-1.jpg)
