---
layout: post
title: "Migrate and Upgrade TFS Collection from TFS 2010 to TFS 11 Beta Video"
date:   2012-04-01 15:12:49 +0100
---

When I downloaded the new [VM of TFS 11 Beta](http://blogs.msdn.com/b/briankel/archive/2012/02/29/visual-studio-11-alm-virtual-machine-and-hands-on-labs-demo-scripts-updated-for-beta.aspx?ocid=soc-n-eg-elite--MRadwan "VM of TFS 11 Beta") provided by [Brian Keller](http://blogs.msdn.com/b/briankel/?ocid=soc-n-eg-elite--MRadwan "Brian Keller"), I didn't find Tailspin Toys. I used to work with Tailspin labs and business, so I decided to migrate and upgrade the TFS Collection from TFS 2010 to [TFS 11 Beta](https://mohamedradwan.com/category/tfs-11-beta/ "TFS 11 Beta links"). I also migrated the DB and the Web Application of Tailspin to the TFS 11 Beta VM.

{% include embed/youtube.html id='s-uZEV8wgHU' %}

When I started to work on the Tailspin team project after the migration, I found that the new user accounts that came with the new VM didn't have permissions to perform most of the tasks on the Tailspin team project. So the following video shows how to give the new user accounts permissions so we can perform the old labs on the new VM (TFS 11 Beta).

{% include embed/youtube.html id='s-cgb0wkajhlM' %}

In order to perform these tasks, you will need the following:

- Virtual Machine of VSALM 11 Beta, from [Brian Keller's blog](http://blogs.msdn.com/b/briankel/archive/2012/02/29/visual-studio-11-alm-virtual-machine-and-hands-on-labs-demo-scripts-updated-for-beta.aspx "TFS 11 Beta VM")
- TFS_Collection that contains the Tailspin Team Project from TFS 2010 VM, [download here](https://skydrive.live.com/redir.aspx?cid=4bcaa16d27b46600&resid=4BCAA16D27B46600!2158&parid=4BCAA16D27B46600!2135 "TFS Collection")
- Tailspin DB, [download here](https://skydrive.live.com/?cid=4bcaa16d27b46600&id=4BCAA16D27B46600%212156 "Tailspin DB")
- Tailspin Web App compiled into 64 bit, [download here](https://skydrive.live.com/redir.aspx?cid=4bcaa16d27b46600&resid=4BCAA16D27B46600!2157&parid=4BCAA16D27B46600!2135 "Tailspin Web App 64 bit")

You can also see some snapshots from the video:

![Login to TFS 2010](/assets/images/2012/04/1-1024x635.png)

![De-attach collection](/assets/images/2012/04/2-1024x669.png)

![De-attach complete](/assets/images/2012/04/3-1024x638.png)

![Take DB offline](/assets/images/2012/04/4-1024x691.png)

![Login to TFS 11 Beta](/assets/images/2012/04/5-1024x670.png)

![Attach Collection](/assets/images/2012/04/6-1024x679.png)

![Attach Collection](/assets/images/2012/04/7-1024x654.png)

![Second Collection Online](/assets/images/2012/04/8-1024x652.png)

![Connect To Second Collection](/assets/images/2012/04/9-1024x653.png)

![Error Because of the Old Process](/assets/images/2012/04/10-1024x659.png)

![Fix the Old Error](/assets/images/2012/04/11-1024x674.png)

![Team Web Access](/assets/images/2012/04/12-1024x657.png)

![Create App Pool](/assets/images/2012/04/13-1024x698.png)

![Tailspin Web Working](/assets/images/2012/04/14-1024x688.png)

To download Visual Studio and TFS 11 Beta, click on the following link:

[http://www.microsoft.com/visualstudio/11/en-us/downloads](http://www.microsoft.com/visualstudio/11/en-us/downloads)
