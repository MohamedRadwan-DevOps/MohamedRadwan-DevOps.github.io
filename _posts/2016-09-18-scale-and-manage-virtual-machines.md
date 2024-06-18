---
layout: post
title: "Scale and Manage Virtual Machines"
date:   2016-09-18 22:43:29 +0100
---

### Introduction 

[**Virtual Machines**](https://mohamedradwan-devops.github.io/2015/09/21/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/) can be scaled and managed using **scale sets**. **Scale sets** are essentially a way for you to manage a set of **Virtual Machines** as a single unit. Before **scale sets**, when you wanted to have a bunch of **virtual machines**, you would spin them up manually or through some script or something and then you would have to manage them yourself but now, **scale sets** have made it very easy to manage hundreds of **virtual machines** at a time. You can also visit **Microsoft Azure website** to learn more about **[Virtual Machine Scale Sets](https://azure.microsoft.com/en-us/documentation/articles/virtual-machine-scale-sets-overview/)** and **[How to Create a Windows Virtual Machine Scale Set using Azure PowerShell](https://azure.microsoft.com/en-us/documentation/articles/virtual-machine-scale-sets-windows-create/)**.

>If you would like to learn more about my personal experience of the Migration Team Foundation Server to Visual Studio Team Services using Database Import Service or TFS Migrator, have a look at this post - [**this post**](https://mohamedradwan-devops.github.io/posts/migrating-team-foundation-server-to-visual-studio-team-services-using-database-import-service-tfs-migrator/).
{: .prompt-tip }


>You can see this video if you would like to find more information about how to develop your first project for Microsoft Dynamics 365 CRM Project. Understand the main components, structure, and process of the development for Microsoft Dynamics 365 CRM. Get the full picture of the development cycle and learn how to create a new CRM solution. In this video, you are going to see how to develop a Dynamic CRM plugin and deploy it to the CRM solution using xrmtoolkit, and how to develop web resources including an HTML page and embed it inside CRM.
{: .prompt-tip }
{% include embed/youtube.html id='OROfBriR_YU' %}

### Part 1: What are Virtual Machine Scale Sets 

**Virtual Machine Scale Sets** are a way to deploy and manage a set of identical **Virtual Machines**. So with **Azure infrastructure service**, if you want fifty **virtual machines**, you normally have to think about networking, storage, extensions, underlying infrastructure and how you configure these **virtual machines** - **virtual machine scale sets** give you a way to create many **virtual machines** and then just configure the properties and manage them as a set. **Scale sets** also integrate with **Azure Autoscale** - this means you can dynamically grow and shrink the pool of **virtual machines**. **Scale sets** also integrate with **Azure Load Balancer**. Another way to look at **scale sets** is an **Azure Compute resource** as part of **Azure Resource Manager**. **Scale sets** are scalable computer layers for hyperscale apps - what that means is if you have a large-scale application with multiple components that use Microsoft services and have different areas that you can configure, you can use **scale sets** to be a generalized computer layer. In a similar way, **scale sets** can be used as an infrastructure for **Platform as a Service (PaaS)**.

![1 what-are-virtual-machine-scale-sets](/assets/images/2016/09/What-are-Virtual-Machine-Scale-Sets-1.jpg "1 what-are-virtual-machine-scale-sets")

>If, after adding a new user to [Dynamics 365](https://dynamics.microsoft.com/en-gb/), you get the following error: *You do not have permissions to see this view. Contact a system administrator crm*, have a look at this post - [**this post**](https://mohamedradwan-devops.github.io/posts/fix-you-do-not-have-permissions-to-see-this-view-contact-a-system-administrator-crm/).
{: .prompt-tip }


>If you would like to learn more about using the [Build Variables](https://docs.microsoft.com/en-us/vsts/build-release/concepts/definitions/build/variables?tabs=batch) in [VSTS](https://www.visualstudio.com/team-services/) and Release Management, have a look at the following post: [VSTS Build variables and Echo](https://mohamedradwan-devops.github.io/posts/vsts-build-variables-and-echo/). The post describes how to see the output at any point in time. While automating a process, through setting variables and displaying them during the build.

### Part 2: Building a Scale Set 

1. Go to **[Azure Quickstart templates GitHub](https://github.com/azure/azure-quickstart-templates)** and select any template. This is a great place to find examples of how to use **Virtual Machine Scale Sets**.

![2-1 Azure-quickstart-templates-GitHub](/assets/images/2016/09/Azure-Quickstart-Templates-Github.jpg "2-1 Azure-quickstart-templates-GitHub")

2. Click on **Deploy to Azure**. This will take you to **Azure Portal**.

![2-2 Deployment-of-VM-scale-set](/assets/images/2016/09/Deployment-of-VM-Scale-Set.jpg "2-2 Deployment-of-VM-scale-set")

3. You will see **Custom Deployment Section**. Click on **Edit Parameters**.
4. Fill out the **parameters** as per your needs.
5. Click on **OK**.
6. Create a **new Resource group**.
7. Type the **name for your Resource group**.
8. Click on **Create**.

![2-3-scale-set-custom-deployment](/assets/images/2016/09/2-3-Scale-Set-Custom-Deployment.jpg "2-3-scale-set-custom-deployment")

9. This is the template deployment so within that three separate **VMs** are going to be made as a set.

![2-4-scale-set-deployment-in-progress](/assets/images/2016/09/2-4-Scale-Set-Deployment-in-Progress.jpg "2-4-scale-set-deployment-in-progress")

10. After deployment, you can see that our **resource group** is listed on the **Azure Portal**.

![2-5-Resource-Group Microsoft Azure](/assets/images/2016/09/2-5-Resource-Group.jpg "2-5-Resource-Group Microsoft Azure")

>If you would like to learn more about different tools and ways for Team Foundation Server to Visual Studio Team Services migration, have a look at the [quick guide about real stories for migrating Team Foundation Server to Visual Studio Team Services](https://mohamedradwan-devops.github.io/posts/published-a-quick-guide-about-real-stories-for-migrating-team-foundation-server-to-visual-studio-team-services/). The guide describes some of the real migration scenarios and explains how to use different tools for several cases.
{: .prompt-tip }


>You can see this video, if you would like to find more information about an overview of Microsoft Dynamics CRM for developers or DevOps Engineers who have never worked with Dynamics CRM before. Learn more about your challenges and how to start developing with Microsoft Dynamics CRM. How the main interface looks like and Admin side (CRM Deployment Manager). Structure of the content of the CRM solution. How to navigate and how to import/export existing CRM solutions (using ALMTollKit or Dynamics 365 Build Tools). How does the process of development look like including an example of a project. Explaining where are located the workflows, plugins, and HTML, CSS, JS, Images. Proposed several approaches for the development process, including with and without build automation.
{: .prompt-tip }
{% include embed/youtube.html id='3FqhZDYLul0' %}

### Conclusion 

**Scale Sets** make it very easy to scale **virtual machines**, they make it very easy to manage and make changes. **Scale sets** are very useful when you want a larger compute unit than just a single **VM**. What batch will do is spin up **scale sets** of the **VMs** so that they can think about hundreds of **VMs** at a time instead of thinking about one **VM** at a time.

>You can see this video, If you would like to find more information about how to install Microsoft Dynamics CRM 365 on Azure VM. Presented installation using SQL 2014 and SQL 2016, on several versions of Windows Server (Windows Server 2012, Windows Server 2012 R2, and Windows Server 2016). Installing Domain Controller, explained all possible issues you may face during the installation. Like incompatible Domain Controller Windows Server 2012 with SQL Server on the same machine, Windows Search Service is not started automatically, installing Dynamics CRM reporting extension. Which was needed to create an additional Dynamics Organization and many other notes.
{: .prompt-tip }
{% include embed/youtube.html id='EGpw9fI-gIY' %}


>If you would like to learn more about enhancing Frontend development code quality.
It includes understanding different types of JavaScript unit testing frameworks like Jasmine, Mocha, Jest, different types of task runner like Grunt and Gulp, different types of linting tools, like JSHint, ESLint, JSLint, CSSLint, different types of code formatter like Prettier and Tidy, how to write your first JavaScript using tests with Jasmine standalone version, how to run JavaScript unit tests using Grunt, Command Line, and PhantomJS, how to calculate code coverage for JavaScript unit tests using Istanbul, how to run JavaScript unit tests using Visual Studio Test Explorer using the chutzpah extension, how to lint JavaScript code using JSHint and how to run that from Command Line using Grunt, finally it shows how to integrate all the quality practices with Visual Studio Team Service Build automation so it can be part of CI/CD or Continuous Integration and Continuous Delivery, have a look at [**this post**](https://mohamedradwan-devops.github.io/2posts/front-end-code-quality-javascript-unit-test-and-linting-automation-with-vsts-build/).
{: .prompt-tip }
