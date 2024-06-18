---
layout: post
title: "Get Started Developing with Visual Studio"
date: 2017-07-24 17:00:36 +0100
---

## Introduction

With the help of **[Visual Studio](https://www.visualstudio.com/vs/older-downloads/)** you can create software using a complete development life cycle, including planning phase, UI design, coding, testing, debugging, analyzing code quality and performance, deploying to customers, and gathering telemetry on usage. Many applications can be created using **Visual Studio**, including but not limited to:

1. Apps and games that run not only on Windows, but also Android and iOS.
2. Websites and web services based on ASP.NET, JQuery, AngularJS, and other popular frameworks.
3. Applications for platforms and devices as diverse as Azure, Office, SharePoint, Hololens, Kinect, and Internet of Things, to name just a few examples.
4. Games and graphics-intensive applications for a variety of Windows devices, including Xbox, using DirectX.

### For anyone still using **Visual Studio 2015** or would like to start with **Visual Studio 2015**

I will explain in this article the basic installation and setup steps.

### More Info 

If you prefer to use Mac, see how it looks in [Visual Studio for Mac](https://mohamedradwan-devops.github.io/posts/visual-studio-for-mac/) post.

### Part 1: Installing Visual Studio 

1. You can download **Visual Studio** by visiting the **[Visual Studio Downloads](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx)**. If you need any help regarding the installation process, you can learn more by visiting the **[Microsoft Developer Network](https://msdn.microsoft.com/en-us/library/e2h7fzkw.aspx)** website.
2. Now that you have downloaded the **Visual Studio installer**, you can double-click on it and start initializing the setup.

![initialize-installation](/assets/images/2016/09/Initialize-installation-3.jpg)

3. It shows you the location where the **Visual Studio IDE** is going to be installed and the different types of installs available. Let's start with the **default install** option that is pre-selected. You can also select **custom install**. **A custom install** will show you a list of features that you can include in your install.
4. Click on **Install**. Installing **Visual Studio** might take a while.

![visual-studio-type-of-installation-default](/assets/images/2016/09/visual-studio-type-of-installation-default.jpg)

>You can see this video if you would like to find more information about how to install Visual Studio 2017 and point to some tricky components. See which Workloads need to be installed and which Individual Components need to be selected additionally. See how to install another Edition of Visual Studio and just put a different nickname in order to distinguish installed editions.
{: .prompt-tip }
{% include embed/youtube.html id='hDujfznIZFE' %}

### Part 2: Launch Visual Studio IDE

1. After installing **Visual Studio** and once your computer has restarted, you can now launch **Visual Studio IDE** for the very first time. Type **visual studio** into your search menu and then click on it.

![type-visual-studio-in-search-menu](/assets/images/2016/09/Type-visual-studio-in-search-menu.jpg)

2. You need to sign in with your **Outlook account**. Type in your email address and password.
3. Click on Sign in.

![sign-in-to-outlook-account](/assets/images/2016/09/Sign-in-to-outlook-account.jpg)

4. Once you have signed in, you will be presented with your **full name**, **contact email**, **region**, and the **option to create a team service site**. You can do whatever you need, but for now click on **Continue**.

![contact-information](/assets/images/2016/09/contact-information.jpg)

5. Let's start with the default theme and click on **Start Visual Studio**.

![visual-studio-environment](/assets/images/2016/09/visual-studio-environment.jpg)

6. **Visual Studio** has got a **start-up page** made up of how to start a project by starting a new project, opening an existing project, or opening it from source control.
7. In the middle of the page, there is **Discover Visual Studio Community resources**. This consists of a bunch of resources that could help you get started.
8. To the right, we have a **solution explorer**.
9. At the bottom of the page, there is an **output window**.
10. In the top right corner, there is a **notification icon**, **send feedback icon**, and the **quick launch search box**. **Notification** provides you with any extension or product updates.
11. **Feedback** is a great way of telling how we are doing.
12. **Quick launch** is a fast way to access menus and features in Visual Studio.

![visual-studio-type-of-installation-default](/assets/images/2016/09/visual-studio-type-of-installation-default-1.jpg)

>You can see this video if you would like to find more information about Visual Studio Code, which is part of the Visual Studio family. The marketplace for the supported extensions is demonstrated, as well as the process of installing, disabling, and reloading the extensions, and starting a new project - a new console application - and debugging this new project.
{: .prompt-tip }
{% include embed/youtube.html id='GWdGSsUxkHE' %}

### Part 3: Create a New Project

1. Go to the **Start Page** and select **New Project**.

![create-new-project](/assets/images/2016/09/create-new-project-1.jpg)

2. Select **Web** under **Templates**.
3. Select **ASP.NET Web Application**.
4. Assign it a suitable **name**.
5. Click on **OK**.

![select-template](/assets/images/2016/09/select-template-1.jpg)

6. Select an **empty template**.
7. Click **OK**.

![select-empty-template](/assets/images/2016/09/select-empty-template.jpg)

8. We have created our very first **Visual Studio Project**!

![new-project-created](/assets/images/2016/09/new-project-created-1.jpg)

>You can see this video If you would like to find more information about the new tools and enhancements for Continuous Delivery (CD) and DevOps with Visual Studio 2017. See how to download and initiate the Continuous Delivery Tools for Visual Studio extension. Create a new team project on VSTS or connect to an existing project. Clone a project to a local Git repository, create a simple web application, and finally how to configure the CD extension. Allowing you to create a Build definition, run that Build, trigger a Release and complete app deployment to the cloud. The process of making changes to the CD and DevOps pipeline is also demonstrated, as well as managing Build failures with the help of the described extension.
{: .prompt-tip }
{% include embed/youtube.html id='I9OAqrAuJT4' %}

### Conclusion 

If you want to find out about new features in **Visual Studio**, see **[What's New in Visual Studio](https://msdn.microsoft.com/en-us/library/bb386063.aspx)**. Also, you can visit the following pages that will help you get started coding:

- **[Make web apps](https://www.visualstudio.com/features/modern-web-tooling-vs)**
- **[Compose cross-platform mobile apps in HTML/Javascript (Apache Cordova)](http://taco.visualstudio.com/en-us/docs/get-started-first-mobile-app/)**
- **[Adjust cross-platform mobile apps in C# or Visual Basic (Xamarin)](https://msdn.microsoft.com/en-us/library/mt299001.aspx)**
- **[Prepare native cross-platform apps and libraries in C++](https://www.visualstudio.com/explore/cplusplus-mdd-vs.aspx)**
- **[Produce games with DirectX](https://msdn.microsoft.com/en-us/library/windows/desktop/ee663274(v=vs.85).aspx)**
- **[Generate games with Unity](https://msdn.microsoft.com/en-us/library/dn940019.aspx)**
- **[Make Universal Windows Platform apps](https://developer.microsoft.com/en-us/windows/windows-apps)**
- **[Arrange desktop applications](https://developer.microsoft.com/en-us/windows/desktop)**
- **[Make Office applications](https://msdn.microsoft.com/en-us/library/fp161347.aspx)**
- **[Tour Visual Studio Team Services and Team Foundation Server](https://www.visualstudio.com/products/visual-studio-team-services-vs)**
