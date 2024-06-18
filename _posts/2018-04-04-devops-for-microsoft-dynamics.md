---
layout: post
title: "DevOps for Microsoft Dynamics"
date: 2018-04-04 07:17:19 +0100
---

## Introduction

DevOps became one of the buzzwords in the software development ecosystem. This is why it's important to consider that with all kinds of development, including custom development for Microsoft Dynamics. So I created a series of videos for new CRM developers to start considering DevOps from the beginning. Also, this series can help DevOps engineers who haven't worked with Dynamics development before.

>If you would like to learn more about how to use PowerShell to change some values for Microsoft Dynamics 365 - have a look at [**this post**](https://mohamedradwan-devops.github.io/posts/working-with-microsoft-dynamics-365-powershell/).
{: .prompt-tip }

## DevOps for Microsoft Dynamics Introduction and abstract 

Introduction and overview of a series of videos about **[Microsoft Dynamics](https://dynamics.microsoft.com/en-gb/)** development, including the overview of the Microsoft Dynamics CRM itself, installing Microsoft Dynamics 2016 on Azure VM and how to upgrade to Dynamics 365, how to develop Dynamics CRM plugin, how to debug Microsoft Dynamics CRM project, create and run unit tests using FakeXRMEasy and [**Microsoft Fakes**](https://msdn.microsoft.com/en-us/library/hh549175.aspx?f=255&MSPPError=-2147217396), JavaScript and front end unit tests as well code quality using JSHint, also how to create and run UI and how to integrate all the practices as part of the [**CI/CD**](https://www.visualstudio.com/team-services/continuous-integration/) [(Continuous Integration and Continuous Delivery)](https://www.visualstudio.com/team-services/continuous-integration/).

{% include embed/youtube.html id='rEJMBwuKY6Y' %}

## 1-What is Microsoft Dynamic CRM for developers who have never worked with CRM before 

Overview of Microsoft Dynamics CRM for developers or DevOps Engineers who have never worked with Dynamics CRM before. Learn more about your challenges and how to start developing with Microsoft Dynamics CRM. How the main interface looks like and Admin side (CRM Deployment Manager). Structure of the content of the CRM solution. How to navigate and how to import/export existing CRM solutions (using ALMToolkit or Dynamics 365 Build Tools). How the development process looks including an example of a project. Explaining where the workflows, plugins, HTML, CSS, JS, and Images are located. Proposed several approaches for the development process, including with and without build automation.

{% include embed/youtube.html id='3FqhZDYLul0' %}


## 2-Installing Microsoft Dynamics CRM 365 for a developer machine on Azure VM 

How to install Microsoft Dynamics CRM 365 on Azure VM. Presented installation using SQL 2014 and SQL 2016, on several versions of Windows Server (Windows Server 2012, Windows Server 2012 R2, and Windows Server 2016). Installing Domain Controller, explained all possible issues which you may face during the installation. Like incompatible Domain Controller Windows Server 2012 with SQL Server on the same machine. Windows Search Service is not started automatically, installing Dynamics CRM reporting extension which was needed to create additional Dynamics Organization and many other notes.

{% include embed/youtube.html id='EGpw9fI-gIY' %}


## 3-Developing Hello World for Microsoft Dynamics 365 CRM Project

How to develop your first project for Microsoft Dynamics 365 CRM Project. Understand the main components, structure, and process of the development for Microsoft Dynamics 365 CRM. Get the full picture of the development cycle and learn how to create a new CRM solution. In this video, you will see how to develop a Dynamic CRM plugin and deploy it to CRM solution using xrmtoolkit, and how to develop web resources including an HTML page and embed it inside CRM.

{% include embed/youtube.html id='OROfBriR_YU' %}



>If, after adding a new user to [Dynamics 365](https://dynamics.microsoft.com/en-gb/), you get the following error: *You do not have permissions to see this view. Contact a system administrator CRM*, have a look at [**this post**](https://mohamedradwan-devops.github.io/posts/fix-you-do-not-have-permissions-to-see-this-view-contact-a-system-administrator-crm/).
{: .prompt-tip }

## 4-Debugging Microsoft Dynamics 365 CRM project

How to debug a Microsoft Dynamics 365 CRM Plugin project. Learn how to put a breakpoint and attach a process to the debugger. We will attach w3wp.exe which is the process of IIS, and the second process is microsoft.crm.sandbox.worker process.exe. Create a new account on CRM and learn where you can see the activities related to the debugging (next to the summary of your account, in the activities tab).

{% include embed/youtube.html id='qpsMA8On2ok' %}


## 5-Creating and running unit test for Microsoft Dynamics 365 CRM 

How to write and run unit tests for Microsoft Dynamics 365 CRM Plugin project using Microsoft Fakes and FakeXRMEasy and integrate them with Visual Studio Team Services build. First, I am going to create a fake context with input and output parameters and execute the plugin using them. FakeXRMEasy is easy and simple since it is based on reflection. In order to work the task properly you need to create an entity "task" and have the Proxy Classes that previously should be added to the project. Using Microsoft Fake, you need to add changes to the code. First, you need to add reference to Microsoft.Xrm.Sdk and after that add Fakes Assembly.

{% include embed/youtube.html id='FQjyaoOmnDQ' %}

## 6-Creating and running UI test for Microsoft Dynamics 365 CRM

How to very easily download the framework and just with small modifications to test the plugin which I have developed in my previous videos. First, I am going to show how to download the EasyRepo framework from the Microsoft GitHub account. After cloning the repo and rebuilding the solution, all UI Automation tests will be displayed in Test Explorer. I will modify the application settings in app.config file (Username, Password, CrmUrl) and edit the existing test for Creating New account adding several lines of code in order to retrieve the activities and assert the associated activities.

{% include embed/youtube.html id='ryWgK34Akt0' %}

## 7-Run Automated UI test as a Continuous Integration & Continuous Delivery Pipeline for Microsoft Dynamics 365

How to integrate automated UI tests with Visual Studio build automation in order to be able to integrate with Continuous Integration & Continuous Delivery Pipeline. First, you need to add a test category and rebuild the application. Note that the build should be configured as a process in order to be able to run the automation UI. See how to create a new build definition using the .NET Desktop template, remove unnecessary tasks, set the correct Test filter criteria, and Test assemblies. Additionally, learn how to use VSTest.Console.exe in order to run the automation form from command line and to debug the failing test.

{% include embed/youtube.html id='tfWCYXxeTmc' %}

>You can find more information about **DevOps** in the following post: [DevOps: The Three Stage Conversation - People, Process, Products](https://mohamedradwan-devops.github.io/posts/devops-the-three-stage-conversation-people-process-products/) which describes the basic principles of **DevOps**. This post will be especially helpful to those for whom DevOps is still a new concept. If you prefer a deeper view on this topic, have a look at the following guide: [quick guide about Basic Principles of DevOps](https://mohamedradwan-devops.github.io/posts/published-a-quick-guide-about-basic-principles-of-devops/), which presents an overview of [DevOps](https://www.visualstudio.com/vs/devops/) process and practices, describing "the big picture", while still maintaining a high level of detail.
{: .prompt-tip }
