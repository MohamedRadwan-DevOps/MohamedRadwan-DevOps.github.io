---
layout: post
title: "Converting My Physical Domain controller to a Virtual machine P2V"
date:   2011-06-23 18:31:34 +0100
---

One of the strongest feature in SCVMM is the ability to convert from
physical machine to virtual machine and this what they called P2V. When
I try to use this feature I have an error that said \"[Boot andor System
volume C was not selected or is not found on source
machine]{style="color:#ff0000;"} \" So after some research I do the
following: Open the CMD on the physical machine after I put the win 2008
DVD on the DVD drive enter the following command

-   `[The drive letter for your DVD drive]`{.variable}:
-   cd boot
-   bootsect /nt52 c: /force

For more information click the following link
[http://support.microsoft.com/kb/942986](http://support.microsoft.com/kb/942986 "Bootsect fix")
But after the machine restarted there was another error that said \"
[NTLDR is missing]{style="color:#ff0000;"}  \" So I restart the machine
with Win DVD on the DVD drive and start repair it with command line tool
and enter the following values

-   bootrec.exe /FixMbr
-   bootrec.exe /FixBoot
-   bootrec.exe /RebuildBcd

For more information click the following link
[http://www.networknet.nl/apps/wp/archives/671](http://www.networknet.nl/apps/wp/archives/671 "NTLDR is missing")
After that I  restart the machine and try the convert again and
everything was very good.

