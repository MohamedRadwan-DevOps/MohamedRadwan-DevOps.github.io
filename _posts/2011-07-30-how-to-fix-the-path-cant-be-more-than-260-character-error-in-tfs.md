---
layout: post
title: "How to fix the path can't be more than 260 character error in TFS"
date:   2011-07-30 13:10:06 +0100
---

I read a good article on how to do that, I just document this
information, thanks [Tarun
Arora](http://geekswithblogs.net/TarunArora/Default.aspx "Tarun Arora")
for pointing to this post and thanks 
[scott.rudy](http://h30507.www3.hp.com/t5/user/viewprofilepage/user-id/31971) To fix the long path you can create a drive on your
computer with the path that you want, for example if I have path like: `C:RadwanWallpaper`

    I can create a file with the following code and save is as .reg and double click it, after reboot, we will find a drive V which point to the wallpaper folder

    ```
    Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINESYSTEMCurrentControlSetControlSession ManagerDOS Devices]
    "V:"="\DosDevices\C:\Radwan\Wallpaper"
    ```

