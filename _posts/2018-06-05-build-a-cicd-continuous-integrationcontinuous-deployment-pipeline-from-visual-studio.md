---
layout: post
title: "Build a CI/CD (Continuous Integration/Continuous Deployment) Pipeline from Visual Studio"
date:   2018-06-05 19:38:17 +0100
---

This article will demonstrate how to build a complete **CI/CD** pipeline in **Visual Studio** and deploy it to [**Azure**](https://azure.microsoft.com/en-us/?v=17.44) using the new [**Continuous Delivery Extension for Visual Studio**](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio). Using [**CI**](https://www.visualstudio.com/learn/what-is-continuous-integration/), allows you to merge the code changes in order to ensure that those changes work with the existing codebase and allows you to perform testing. On the other hand, using [**CD**](https://www.visualstudio.com/learn/what-is-continuous-delivery/) you are repeatedly pushing code through a deployment pipeline where it is built, tested, and deployed afterwards. This [**CI/CD**](https://www.visualstudio.com/team-services/continuous-integration/) team practice automates the build, testing and deployment of your application, and allows complete traceability in order to see code changes, reviews and test results.

In order to create a **CI** build and a release pipeline and [**Release Management**](https://mohamedradwan-devops.github.io/2016/07/24/difference-between-continuous-deployment-and-release-management/) that is going to deploy the code into **Azure**, all you need is an existing web-based application and an extension from the marketplace. *Otherwise, you can always contact the experts that offer end-to-end [DevOps consulting services](https://www.scnsoft.com/services/devops-consulting) based on the modern methodologies designed to deliver high-quality software faster.*

> For more information about how to work with Kubernetes cluster and deploy it to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see **[Kubernetes cluster for beginner](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service)
{: .prompt-info }

{% include embed/youtube.html id='4DUhc0MjdUc' %}

## Step 1: Enable Continuous Delivery extension for Visual Studio

In order to use **Continuous Delivery Tools for Visual Studio** extension you just need to enable it. The **Continuous Delivery Tools for Visual Studio** extension makes it simple to automate and stay up to date on your [**DevOps**](https://www.visualstudio.com/learn/what-is-devops/) pipeline for **[ASP.NET](https://mohamedradwan-devops.github.io/2010/05/14/multiple-web-config-with-asp-net-and-visual-studio-2010/)** and other projects targeting **Azure**. The tools also allow you to improve your code quality and security.

1.  Go to **Tools**, choose **Extensions and Updates**.
2.  From the prompted window, select **Continuous Delivery Tools for Visual Studio** and click **Enable**.

*If you don't have installed Continuous Delivery Tools go to [**Online Visual Studio Marketplace**](https://marketplace.visualstudio.com/), search for "Continuous" and download it.

[![1-Enable Continuous Delivery Tools for Visual Studio](/assets/img/2017/12/1-Enable-Continuous-Delivery-Tools-for-Visual-Studio-1024x578.jpg)](/assets/img/2017/12/1-Enable-Continuous-Delivery-Tools-for-Visual-Studio.jpg)

## Step 2: Create a project in Team Services

In this step you are going to create a project in [Team Services](https://mohamedradwan-devops.github.io/posts/release-management-overview-for-tfs-and-vsts/) and put your project code there without leaving your IDE. Team Services is a tool that allows you to build a **continuous integration** and **continuous delivery**.

1.  Go in the **Solution Explorer**, right-click on your web-based project.
2.  Click on the new context menu **Configure Continuous Delivery.**
3.  New window is displayed **Configure Continuous Delivery.** Click on the **Add this project to source control** plus button.

[![2.1-Add project to Source Control and Configure Continuous Delivery](/assets/img/2017/12/2.1-Add-project-to-Source-Control-and-Configure-Continuous-Delivery-1024x578.jpg)](/assets/img/2017/12/2.1-Add-project-to-Source-Control-and-Configure-Continuous-Delivery.jpg)

4.  Click on the **Publish Git Repo** button located in the **Publish to Visual Studio Team Services** section in **Team Explorer.**
5.  Your **Microsoft Account** is automatically fetched from your IDE. Also is displayed the **Team Services Domain** which will be used and your **Repository Name**. Click on the **Publish Repository** button in order to create a project in **Team Services**.
6.  After the synchronization is finished you will see that your project is created in the Team Explorer.

[![2.2 -Create project in Team Services](/assets/img/2017/12/2.2-Create-project-in-Team-Services.jpg)](/assets/img/2017/12/2.2-Create-project-in-Team-Services.jpg)

Now your project is created into **Team Services** account (the source code is uploaded, there is a **Git Repository** and it is generating continuous delivery pipeline automatically).

7.  In the output window you can see that your **CI/CD** are setting up for your project.
8.  After a while, you are going to get 3 different links:

-   Link to the **build**
-   Link to the **release**
-   Link to the assets created in **Azure** which is going to be the target for your deployment. (application service)

[![2.3-Linking Continiuos Delivery to the Build, Release and Azure Assets](/assets/img/2017/12/2.3-Linking-Continiuos-Delivery-to-the-Build-Release-and-Azure-Assets-1024x578.jpg)](/assets/img/2017/12/2.3-Linking-Continiuos-Delivery-to-the-Build-Release-and-Azure-Assets.jpg)


> For more information about how to work with **Docker** like, pull docker image, run docker image and work with container, see **[Docker for beginners](https://mohamedradwan-devops.github.io/posts/docker-for-beginners-step-by-step-tutorial/)
{: .prompt-info }

{% include embed/youtube.html id='3RJv6yVfaRE' %}

## Step 3: Open the project in Team Services

A **[build](https://mohamedradwan-devops.github.io/2015/06/16/changing-the-connection-string-during-the-tfs-build-for-the-publish-profile-of-the-ssdt-sql-server-data-tool/) definition** is the entity through which you define your automated **build process**. In the build definition, you compose a set of **tasks**, each of which perform a step in your build.

1.  Choose the **Build Definition** link provided in Output window and copy.
2.  Paste it in a browser in order to open the project containing your application in Team Services.
3.  The summary for the build definition is displayed. You can see that the build is already running.
4.  Click on the build link.

[![3.1-Build definition summary in Team Services](/assets/img/2017/12/3.1-Build-definition-summary-in-Team-Services-1024x579.jpg)](/assets/img/2017/12/3.1-Build-definition-summary-in-Team-Services.jpg)

5.  It is shown an output of your build server which is running your build automatically.
6.  Click on the **Edit build definition.**

[![3.2-Editing Build Definition in Team Services](/assets/img/2017/12/3.2-Editing-Build-Definition-in-Team-Services-1024x578.jpg)](/assets/img/2017/12/3.2-Editing-Build-Definition-in-Team-Services.jpg)

7.  You are going to see all the **tasks** that were automatically set up in order to be able to build the code that you had inside your Visual Studio. You can:

-   Add additional task
-   Customize the tasks that are already there

[![3.3-Customizing the tasks of Build Process](/assets/img/2017/12/3.3-Customizing-the-tasks-of-Build-Process-1024x579.jpg)](/assets/img/2017/12/3.3-Customizing-the-tasks-of-Build-Process.jpg)

## Step 4: Test Assemblies Task

Each task has a **Version** selector that enables you to specify the major version of the task used in your build or deployment. When a new minor version is released (for example, 1.2 to 1.3), your build or release will automatically use the new version. However, if a new major **version** is released (for example 2.0), your build or release will continue to use the major version you specified until you edit the definition and manually change to the new major version.

1.  Click on the **Test Assemblies.**
2.  You can see a little flag icon which means that there is a new available preview version of this task. Click on the Flag Icon and choose version 2\* in order to preview.

[![4.1-Visual Studio Test Asesemblies Tasks](/assets/img/2017/12/4.1-Visual-Studio-Test-Asesemblies-Tasks-1024x579.jpg)](/assets/img/2017/12/4.1-Visual-Studio-Test-Asesemblies-Tasks.jpg)

3.  There are several new items shown for the **Test Assemblies** One of them is **Run only impacted tests.** This is an item which allows tools to analyze which lines of code were changed against the tests that were run in the past and you will know which tests execute which lines of code (you will not have to run all of your tests, you are able to run only the tests that were impacted with the changes).
4.  **Run tests in parallel on multi-core machines** is an item which allows your tests to run in such a way to use all the cores you have available. Using this item you will effectively increase the number of tests running at the same time, which will reduce the time to run all the tests.

[![4.2-Visual Studio Test Assemblies Items](/assets/img/2017/12/4.2-Visual-Studio-Test-Assemblies-Items-1024x578.jpg)](/assets/img/2017/12/4.2-Visual-Studio-Test-Assemblies-Items.jpg)

5.  **[Code coverage](https://mohamedradwan-devops.github.io/2010/10/27/code-coverage-with-team-build-and-mvc-or-any-web-application/) enabled** is another very useful item that during executing your unit test, VSTS will monitor the code as it is being tested and highlight which lines of code were actually covered with your tests.

[![4.3-Visual Stuido Coverage of Test Assemblies Items](/assets/img/2017/12/4.3-Visual-Stuido-Coverage-of-Test-Assemblies-Items-1024x578.jpg)](/assets/img/2017/12/4.3-Visual-Stuido-Coverage-of-Test-Assemblies-Items.jpg)

## Step 5: Add additional task

A **task** is the building block for defining automation in a build definition, or in an environment of a release definition. A task is simply a packaged script or procedure that has been abstracted with a set of inputs. There are some built-in tasks in order to enable fundamental build and deployment scenarios.

1.  Click on the **Add Task** plus button in order to create new additional task.
2.  An enormous list of tasks is displayed that can be run out of the box that allow you to target any language/platform. (Chef support, CocoaPods, Docker, NodeJS, Java).
3.  If you want to install another feature or extension which is not listed, simply click on the link **Check out our Marketplace** which is displayed above the list of tasks.

[![5.1-Adding additional task in build definition](/assets/img/2017/12/5.1-Adding-additional-task-in-build-definition-1024x578.jpg)](/assets/img/2017/12/5.1-Adding-additional-task-in-build-definition.jpg)

4.  In new tab is opened [**Visual Studio Marketplace**](https://marketplace.visualstudio.com/) with all additional features and extensions. All of them are open source and you can actually go to [**GitHub**](https://github.com/Microsoft) and see their source code. You also can write your own task using PowerShell or NodeJS.

[![5.2-Visual Studio Marketplace extensions](/assets/img/2017/12/5.2-Visual-Studio-Marketplace-extensions-1024x578.jpg)](/assets/img/2017/12/5.2-Visual-Studio-Marketplace-extensions.jpg)


> For more information about how to work with **Git** with animation. All commands will be represented in graphical animation. E.g. git branch, git merge, git rebase, git cherry-pick and many others, see **[Mastering Git with animation](https://mohamedradwan-devops.github.io/posts/mastering-git-from-beginner-to-advanced-step-by-step-with-graphical-animation-commands/)
{: .prompt-info }

{% include embed/youtube.html id='ZgCCnv9LxzA' %}

## Step 6: Setting encrypted and none encrypted Variables

**Variables** are a great way to store and share key bits of data in your build definition. Some build templates automatically define some variables for you.

1.  Go and click on the second tab named **Variables** (next to the tab Tasks).
2.  Click on the padlock located next to the variable value, in order to encrypt it.
3.  After encrypting, the value of the variable is displayed with asterisks, and no one can see this value except the person who encrypted it.

[![6-Encrypting Variables in Build Definitions](/assets/img/2017/12/6-Encrypting-Variables-in-Build-Definitions-1024x578.jpg)](/assets/img/2017/12/6-Encrypting-Variables-in-Build-Definitions.jpg)

## Step 7: Turn on the Continuous Integration (CI) Trigger

On the **Triggers** tab you specify the events that will trigger the build. You can use the same build definition for both CI and scheduled builds.

1.  Go and click on the third tab named **Triggers**, where actually you can setup your **Continuous Integration**.
2.  Enable the box **Disable this trigger** means that this build will run automatically whenever someone checks in code or with other words when a new version of the source artifacts is available.

[![7-Setting up Continuous Integration Triggers](/assets/img/2017/12/7-Setting-up-Continuous-Integration-Triggers-1024x578.jpg)](/assets/img/2017/12/7-Setting-up-Continuous-Integration-Triggers.jpg)

## Step 8: Build Definition Options

If the build process fails, you can automatically create a work item to track getting the problem fixed. You can specify the work item type. You can also select if you want to assign the work item to the requestor. For example, if this is a **CI build**, and a team member checks in some code that breaks the build, then the work item is assigned to that person.

1.  Go and click on the fourth tab named **Options**.
2.  Enable the box **Create Work Item on Failure.** CI builds are supposed to build at every check in, and if some of them fail because the developer made an error, you can automatically create a work item in order to track getting the problem fixed.
3.  **Default agent queue** option is displayed in the second half of the **Options**. In the drop down list are listed all available pools:
    -   **Default** (if your team uses private agents set up by your own)
    -   [**Hosted**](https://docs.microsoft.com/en-us/vsts/build-release/concepts/agents/hosted) (Windows based machine, if your team uses VS2017 or VS2015)
    -   [**Hosted Linux Preview**](https://docs.microsoft.com/en-us/vsts/build-release/concepts/agents/hosted) (if your team uses development tools on Ubuntu)
    -   [**Hosted VS2017**](https://docs.microsoft.com/en-us/vsts/build-release/concepts/agents/hosted) (if your team uses Visual Studio 2017)

[![8-Creating a work item on failure of Build Definition](/assets/img/2017/12/8-Creating-a-work-item-on-failure-of-Build-Definition-1024x578.jpg)](/assets/img/2017/12/8-Creating-a-work-item-on-failure-of-Build-Definition.jpg)

## Step 9: Build Summary

You can see the summary of the **build**, in other words everything that happened during the build, following the next steps:

1.  Click on the **Summary** button located in the upper right corner.

[![9.1-Opening Build Summary](/assets/img/2017/12/9.1-Opening-Build-Summary-1024x77.jpg)](/assets/img/2017/12/9.1-Opening-Build-Summary.jpg)

2.  Click on the **build number**, located in the **Recently completed.**

[![9.2-Short Build Summary](/assets/img/2017/12/9.2-Short-Build-Summary.jpg)](/assets/img/2017/12/9.2-Short-Build-Summary.jpg)

3.  The build summary is displayed. You are able to see:

-   Code coverage
-   All work items and tasks
-   Deployments

[![9.3-Build Summary with Associated changes, Code Coverage and Deployments](/assets/img/2017/12/9.3-Build-Summary-with-Associated-changes-Code-Coverage-and-Deployments-1024x578.jpg)](/assets/img/2017/12/9.3-Build-Summary-with-Associated-changes-Code-Coverage-and-Deployments.jpg)


> For more information about DevOps, what is DevOps, how to work with DevOps, what is Continuous Integration and what is Continuous Delivery. What is the difference between CI pipelines and CD pipelines and many other topics. See **[DevOps for beginner](https://mohamedradwan-devops.github.io/posts/devops-tutorial-for-beginners-developing-ci-cd-pipelines-continuous-integration-and-deployment/)
{: .prompt-info }

{% include embed/youtube.html id='8gQEOsRQqFM' %}

## Step 10: Release definition

A **release definition** is one of the fundamental concepts in Release Management for VSTS and TFS. It defines the end-to-end release process for an application to be deployed across various environments. Remember that you as a developer, never have to leave VS in order to deploy an application from VS into Azure.

1.  Click on the succeeded deployment link, displayed in the Build Summary page, in the Deployments section. This is a **CD** portion of a **CI/CD**.

[![10.1-Opening Release Definition](/assets/img/2017/12/10.1-Opening-Release-Definition-1024x578.jpg)](/assets/img/2017/12/10.1-Opening-Release-Definition.jpg)

2.  A **release definition** is displayed that deployed the code into **Azure**.
3.  Click on the three dots located next to the particular release definition.
4.  From the displayed context menu, select **Edit**.

[![10.2-Editing Release Definition](/assets/img/2017/12/10.2-Editing-Release-Definition-1024x578.jpg)](/assets/img/2017/12/10.2-Editing-Release-Definition.jpg)

5.  The deployment is very similar to the build system. All it does is taking a result of CI and deploying it in Azure using CD. In this page there are displayed:

-   Series of environments
-   Tasks that you want to perform in each environment

[![10.3-Deploying result of CI into Azure using CD](/assets/img/2017/12/10.3-Deploying-result-of-CI-into-Azure-using-CD-1024x578.jpg)](/assets/img/2017/12/10.3-Deploying-result-of-CI-into-Azure-using-CD.jpg)

## Step 11: Check if the application is really deployed from Visual Studio into Azure

**Microsoft Azure** is a cloud computing service for building, testing, deploying, and managing applications and services through a global network of Microsoft-managed data centers. In this step you will verify if your web application is deployed in **Azure**, following the next steps:

1.  Go in your **Azure portal.**
2.  Click on the **Resource Groups.**
3.  Search for the "demo".
4.  Click In the search results on your web project "e2edemo".
5.  Open the web application link.

[![11.1-Logging into Azure portal](/assets/img/2017/12/11.1-Logging-into-Azure-portal-1024x578.jpg)](/assets/img/2017/12/11.1-Logging-into-Azure-portal.jpg)

6.  Click on the **Browse** button displayed in the upper menu.

[![11.2-Browsing for deployed application in Azure](/assets/img/2017/12/11.2-Browsing-for-deployed-application-in-Azure-1024x579.jpg)](/assets/img/2017/12/11.2-Browsing-for-deployed-application-in-Azure.jpg)

7.  The website which code is running in your Visual Studio should be opened, now hosted in Azure. Now every change that developer makes will immediately be deployed inside **Azure environment**, which is giving you a true **Continuous Delivery**.

[![11.3-Deployed application](/assets/img/2017/12/11.3-Deployed-application-1024x578.jpg)](/assets/img/2017/12/11.3-Deployed-application.jpg)

## Conclusion

**Continuous Integration** is a software development practice in which you build and test software every time a developer pushes code to the application. **Continuous Delivery** is a software engineering approach in which continuous integration, automated testing, and automated deployment capabilities allow software to be developed and deployed rapidly, reliably, and repeatedly with minimal human intervention.

High-performing teams usually practice **Continuous Integration (CI)** and **Continuous Delivery (CD)**. VSTS not only automates the build, testing and deployment of your application, but it gives you complete traceability to see everything in the build including changes to your code, reviews, and test results, as a tool which is fully supporting [DevOps](https://mohamedradwan-devops.github.io/2016/09/28/what-is-devops/) practices.
