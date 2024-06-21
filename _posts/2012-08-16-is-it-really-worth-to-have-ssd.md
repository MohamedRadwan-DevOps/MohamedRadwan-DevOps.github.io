---
layout: post
title: "Is it really worth to have SSD?"
date: 2012-08-16 02:19:57 +0100
---

![SSD-Corsair240GT](/assets/img/2012/08/ssd-corsair240gt.jpg){.alignnone .wp-image-2321 width="181" height="219"}

In a previous post, I talked about ["Being fast, it\'s not optional for us!!!"](https://mohamedradwan-devops.github.io/2012/08/09/being-fast-its-not-an-option-for-us/ "Being fast, it's not optional for us!!!"). Today I will just show the benefit of the SSD, so just see the following video for copying 7 GB between SSDs.

{% include embed/youtube.html id='F_RZNoR59zI' %}

Just imagine now the loading time of any application that reads or writes from and to an [SSD](http://en.wikipedia.org/wiki/Solid-state_drive "SSD"). If you don\'t have it **GET IT NOW!!** [Andrew Whitten](http://andrewwhitten.wordpress.com/ "Andrew Whitten") wrote a good blog post about just testing and timing some simple operations in [Windows 8](http://windows.microsoft.com/en-US/windows/home "Windows 8") that anyone can do out of the box. 

**Here a part of the post:**

**Results** 
The results in seconds are below:

| **Test**                                          | **Intel X-25-M (SSD)**   | **WD e-Sata**   | **WD Passport USB3**   | **WD Passport USB2**   |
|---------------------------------------------------|--------------------------|-----------------|------------------------|------------------------|
| **Windows Startup**                               | 10                       | 21              | 26                     | 35                     |
| **Windows Login**                                 | 5                        | 4               | 5                      | 8                      |
| **Launch Visual Studio 11**                       | 6                        | 24              | 26                     | 36                     |
| **Build basic HTML5 solution in Visual Studio**   | 1                        | 4               | 4                      | 7                      |
| **Launch Expression Blend 5**                     | 2                        | 8               | 15                     | 19                     |
| **Total**                                         | **23**                   | **61**          | **76**                 | **105**                |

**Conclusion** 
There is a considerable speed advantage to using a Solid State Disk for running your [Hyper-V](http://technet.microsoft.com/en-us/library/hh831531.aspx "Hyper-V Overview") virtual machines. e-Sata still proved to be slightly faster than USB 3. Surprisingly, USB 2 was not extremely slow compared to its USB 3 successor. So we can see the benefit of the SSD on normal PCs and SSD with virtual machines and Hyper-V. So I believe it really is worth it!
