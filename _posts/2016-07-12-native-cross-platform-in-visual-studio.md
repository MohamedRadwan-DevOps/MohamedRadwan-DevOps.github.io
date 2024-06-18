---
layout: post
title: "Native Cross-Platform in Visual Studio"
date:   2016-07-12 15:42:51 +0100
---

### Introduction 

In **[Visual Studio 2015](https://www.visualstudio.com/)** you can build same apps for different devices, such as **Android**, **iOS**, and **Windows**. In design process you will have the access to many design tools in **Visual Studio** that will allow you to add many connected services, like **[Azure Mobile Services](https://azure.microsoft.com/en-us/documentation/learning-paths/appservice-mobileapps/)**, **Application Insights** and **Office 365**. What is really good is that you don\'t have to use specific coding language, you can use your preferred coding language, such as **C#** and the **.**NET Framework, **HTML** and **JavaScript**, or **C++**. You can even share code, images, strings and even the user interface in some cases. 

![0-Native Cross-Platform in Visual Studio](/assets/images/2016/07/0-Native-Cross-Platform-in-Visual-Studio.jpg "0-Native Cross-Platform in Visual Studio")

>If you would like to start using [Visual Studio](https://www.visualstudio.com/) for developing, read the details about its installation, launching and creating a new project in my post [Get Started Developing with Visual Studio](https://mohamedradwan-devops.github.io/posts/get-started-developing-with-visual-studio-2015/). If you prefer to use Mac, see how it looks in [Visual Studio for Mac](https://mohamedradwan-devops.github.io/posts/visual-studio-for-mac/) post.
{: .prompt-tip }


>If you want to know more about maintaining the backlog in a proper way, you can visit the following post: [Key Tips For Maintaining Good Product Backlog in Agile and Scrum](https://mohamedradwan-devops.github.io/posts/key-tips-for-maintaining-good-product-backlog-in-agile-and-scrum/). The post describes a way to efficiently organize the [backlog](https://docs.microsoft.com/en-us/vsts/work/backlogs/create-your-backlog) items allowing you to understand the requirements better, and providing you with higher level of detail of what is actually expected from the work or delivery perspective.
{: .prompt-info }


### Working with HTML and JavaScript

If you don\'t have **[Visual Studio 2015](https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs.aspx)** installed yet, you will have to download and install it first. In setup process choose **HTML/JavaScript** (**Apache Cordova**) feature. Apache Cordova is a framework which is including a plug-in model. That enables the sharing of files for other types of web applications, without having to redesign or modify them. After you created your first project and you want to run your app, you can choose between different emulators to do that or you can even run it in a browser or on a device which is connected directly to your computer. The most used emulators are **Apache Ripple emulator** or **Visual Studio Emulator** and they are used for **Android** or **Windows Phone**. 

![1-HTML and JavaScript Apache Cordova Visual Studio](/assets/images/2016/07/1-HTML-and-JavaScript-Apache-Cordova-Visual-Studio.jpg)

>You can see this video, if you would like to find more information about how to upload VSTS extension to VSTS Marketplace with the publisher ID. Share it and install it afterwards as VSTS extension. From the appropriate publisher ID upload the previously packaged extension into VSIX. See how to share the uploaded extension. (which is still private) with VSTS account and how to see with which accounts the extension is already shared with.
{: .prompt-info }
{% include embed/youtube.html id='0EZdEPfyBFI' %}

>The post [User stories in Agile world](https://mohamedradwan-devops.github.io/posts/user-stories-in-agile-world/) focuses on an important unit of Agile software development process, which is [User Story](https://docs.microsoft.com/en-us/vsts/work/work-items/guidance/agile-process-workflow). The post also describes some basic rules and recommendations you have to follow before adding the descriptions of **PBI**.
{: .prompt-tip }
{% include embed/youtube.html id='0EZdEPfyBFI' %}

### Working with .NET framework / Xamarin 

First you will need to have installed **Visual Studio 2015**. In installation process you will have to choose Custom installation and select **Cross Platform Mobile Development > C#/.NET** or you can simply use the **[Xamarin Installer](https://www.xamarin.com/download)**. If you already have **Visual Studio 2015** installed, in Programs and Features select the same Custom option for **Xamarin** as above. When you\'ll create new project and when you will want to see how it works, you can use the Android **emulator for Android apps**, for Windows you can run apps natively or also you can use **Windows Phone emulator**. For **iOS** project you will start **Mac emulator** and you will have to connect to a networked **Mac**. 

![2-Xamarin Native Cross-Platform in Visual Studio](/assets/images/2016/07/2-Xamarin-Native-Cross-Platform-in-Visual-Studio.jpg)

### Working with Visual C++

Again you will have to have first installed **Visual Studio 2015** and also in this case you will have to install the **Visual C++ for Cross Platform Mobile Development tools**. This option is available for now **only for Android or Windows app**, it\'s not yet available for **iOS apps**. You will have the chance to choose between many templates, some of them are native and can be used for both solutions (Android and Windows) and some of them targets on **Windows**. When your project is ready and you want to see how it looks, you can use **Visual Studio Emulator** for **Android** or **Windows**. 

![3-Working with Visual C++ Visual Studio](/assets/images/2016/07/3-Working-with-Visual-C-Visual-Studio.jpg)

>You can see this video, if you would like to find more information about how to create a Publisher Id for the Continuous Delivery purposes. See how to create a Publisher ID in order to be able to publish an extension to VSTS marketplace. Learn the differences between Private and Public Publisher Id. Any Publisher Id when first is created is Private. And afterwards if we want to make it Public we need to send a request to Microsoft to verify our identity (as Individual or a Company).
{: .prompt-info }
{% include embed/youtube.html id='AMP_eNG0Ba0' %}

[Tip]{.ion-tip} In some of the previous posts you can find high-level descriptions of [Agile](https://mohamedradwan-devops.github.io/posts/quick-intro-to-agile/) principles and the usage of some [Agile tools](https://mohamedradwan-devops.github.io/posts/tfs-2015-agile-project-management/) and [Agile methodology](http://agilemanifesto.org/).
{: .prompt-tip }


### Conclusion 

The native cross platforms were a big improvement for many developers. In the old **Visual Studio Build system** was pretty hard to do open source and cross platform tasks. This solution is really out of the box and it was major step forward, especially when building app for **iOS**. Previously you would have to be on **Mac** to build **iOS app**. But now this is all possible with this cross-platforms in **Visual Studio 2015**.

>Read detailed explanation about all types of **Scrum and Agile meetings** (Sprint Planning, Stand-up, Grooming, [Sprint Review](https://docs.microsoft.com/en-us/vsts/work/scrum/sprint-planning), Retrospective Meeting) in my past post [Types of meetings in Scrum and Agile](https://mohamedradwan-devops.github.io/posts/types-of-meetings-in-scrum-and-agile/).
{: .prompt-tip }

>You can see this video, if you would like to find more information about walkthrough about how to install Windows Server 2016 on a virtual machine. See how to insert and load iso file by opening the virtual machine using Hyper-V manager. Do not forget after the installation is finished and virtual machine restarted. To check for windows updates in order to have the last version. And to change the virtual machine name in order to match the standard of your organization.
{: .prompt-info }
{% include embed/youtube.html id='Zd6IgG1ifkY' %}
