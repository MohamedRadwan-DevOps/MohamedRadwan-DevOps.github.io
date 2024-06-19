---
layout: post
title: "Create a VHD and add it to the Boot menu using bcdedit command"
date:   2012-02-23 14:38:24 +0100
---

Let\'s list the steps

1.  Create a VHD from Disk++Management
2.  Or create a VHD from Command line using diskpart command
3.  Attach the VHD if you already have an existing VHD using Disk
    Management
4.  Or attach VHD using Command line
5.  Copy a BCD entry and edit it according to the new value

-   Create a VHD from Disk Managment

We can create the VHD from the Disk Management from computer++management,
see the following link
[http://www.sevenforums.com/tutorials/566-virtual-hard-disk-create-attach-vhd.html](http://www.sevenforums.com/tutorials/566-virtual-hard-disk-create-attach-vhd.html)

-   Or create VHD from Command line using diskpart command

```
create vdisk file=\"D:pathToVhd.vhd\"
type=expandable maximum=maxsizeInMegabyte
```

For more information see the following link [Windows 7 - VHD Boot - Setup
Guideline](http://blogs.msdn.com/b/knom/archive/2009/04/07/windows-7-vhd-boot-setup-guideline.aspx?ocid=soc-n-eg-elite--MRadwan "Windows 7 - VHD Boot - Setup Guideline")

-   Attach the VHD if you already have an existing VHD using
    Disk++Management

You can see the first link

-   Or attach VHD using Command line

```
Iskpart select vdisk
file=c:windows7.vhd attach vdisk list volume select volume
\<volume_number_of_attached_VHD\> assign letter=v exit

```

-   Copy a BCD entry and edit it according to the new value



First we will see the existing entries by command bcdedit, this will
list all existing entries, then we will select the++entry++for the same
windows for example I will++select++the++entry++of windows 7 and copy it and
then change it\'s value to the new value,++remember++that we used the GUID
to do this

```
bcdedit /copy {originalguid} /d \"New
Windows 7 Installation\" bcdedit /set {newguid} device
vhd=\[D:\]Image.vhd bcdedit /set {newguid} osdevice vhd=\[D:\]Image.vhd
bcdedit /set {newguid} detecthal on
```

Fore more information about bcedit command see the following link
<http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html>
<http://technet.microsoft.com/en-us/library/dd799299(v=ws.10).aspx>
[DiskPart
help](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/diskpart.mspx?mfr=true)

