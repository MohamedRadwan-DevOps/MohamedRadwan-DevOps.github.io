---
layout: post
title: "What is Application Lifecycle Management (ALM)"
date: 2016-08-01 17:31:56 +0100
---

### Introduction {#Intro}

Change is pervasive in competitive markets. In business we talk about the value of change, the necessity of change and driving the change. In an age of global distributed enterprise, relentless demands for efficiency and rigorous compliance mandates. Mastering change is strategic imperative so why is it so difficult for businesses to manage change. Because change is accompanied by many challenges, competitive threats, best practices implementation. **Application Lifecycle Management** (ALM) and [DevOps](https://mohamedradwan-devops.github.io/posts/devops-framework-and-practices/) solutions automate the entire process around software delivery and change management. You can also visit [Visual Studio website](https://www.visualstudio.com/en-us/features/alm-devops-vs.aspx) to have a deeper insight of DevOps and Application Lifecycle Management (ALM).

![0-Application Lifecycle Management Continuously Deliver](/assets/images/2016/08/0-Application-Lifecycle-Management-Continuously-Deliver.jpg "0-Application Lifecycle Management Continuously Deliver")

>There are many [**VSTS extensions**](https://marketplace.visualstudio.com/vsts) designed to make the work process easier. One of them is the **Delivery Plans** extension providing a better cross-team visibility. Read more about it in my post [Delivery Plans Extension for VSTS](https://mohamedradwan-devops.github.io/2017/07/13/delivery-plans-extension-for-vsts/) and learn how to manage more than one team in a much easier way.
{: .prompt-tip }

>You can see this video, if you would like to find more information about how to write your first JavaScript unit test using Jasmine as a BDD or Behavior Driven Development framework, how to use Jasmine standalone version, how to reference the code under test, how to change the configuration in specrunner.html file, you will see also, how to use beforeEach to inject the needed elements of the DOM of the HTML and how to remove them using afterEach after ran the tests, this video is prerequisite for all the coming videos if you don’t know Jasmine.
{: .prompt-info }
{% include embed/youtube.html id='f6f46eRxBCg' %}

### What is Application Lifecycle Management (ALM) 

Application lifecycle management (ALM) is the supervision of a software application from its initial planning through retirement. It is a help to get everything you need in one solution. with agile planning, source code control build test and automated release to have regular integration, testing, delivery and monitoring of your application. It supports all famous test frameworks, such as Junit, Selenium, Jasmine, xUnit and Mochat. So that you are able to test any of the project types along the way with the deployment. It also refers to how changes to an application are documented and tracked. As you are building software iteratively you are getting continuous feedback that is going to flow back into the development team and give you insights into what you can make better in the next iteration or bugs that you need to fix. New features that you might need to add. A much better way, a more accurate a clear way to think about ALM is to view it as having four-parts: 1. Plan 2. Develop + Test 3. Release 4. Monitor + Learn

![Application Lifecycle Management](/assets/images/2016/08/Application-Lifecycle-Management.jpg "Application Lifecycle Management")

>If you would like to know more about the best practices for [DevOps](https://www.visualstudio.com/team-services/devops/), Continuous Integration and Continuous Delivery, you can have a look at the following post: [Configure CI (Continuous Integration) and CD (Continuous Delivery Pipeline)](https://mohamedradwan-devops.github.io/posts/develop-vsts-extension-and-configure-ci-continuous-integration-and-cd-continuous-delivery-pipeline/).
{: .prompt-info }

>In order to ensure [**Continuous Integration**](https://www.visualstudio.com/team-services/continuous-integration/) we need to use proper **deploying strategy**. Read more about deploying with Feature Branches and Feature Toggle in the following post; [Deploy from Branches with and without Feature Toggle](https://mohamedradwan-devops.github.io/posts/promoting-your-application-deployment-to-different-environments-from-branches-with-and-without-feature-toggle/).
{: .prompt-tip }

This phases of software development are used for quite some time. In every case you need first to plan, develop and test, release and after that to monitor and learn. The change **DevOps** is including every involved member and how the team is working together in the whole process of software development. In the release phase the are different steps that are implemented, but not necessary all those steps are implemented in all cases. In **Automated functional testing phase** the unit is testing different components in the build process. Which means that different components need to come together and to make sure that they work together well. **Cloud Load Testing** allows you to test product before the product actually goes into production to know that the code can handle the load.

![1-Release phase of Application Lifecycle Management](/assets/images/2016/08/1-Release-phase-of-Application-Lifecycle-Management.jpg "1-Release phase of Application Lifecycle Management")

The first thing that happens after the idea is typically business case development and its planning. An organization must decide whether an app is worth creating. At some point a decision is made to approve the project. Development kicks off then and governance become project portfolio management. Once the app is deployed in most organizations it is subject to what’s become known as application portfolio management. The process of keeping track of all of your apps making decisions about which ones get what resources for update and so on and ultimately for making the final decision when to pull the plug on this app. Governance, making decisions runs throughout the entire ALM cycle.

>You can see this video, If you would like to find more information about how run JavaScript Unit test written in Jasmine from Command Line using Grunt and PhantomJS, it includes, how to install Node.js with NPM (Node Package Manager), how to install Grunt CLI (Command Line Interface), how to install contrib-jasmine npm, how to create Node.js default configuration file (packages.json), how to create the first Gruntfile.js configuration file, how to set the configuration to run Jasmine inside Gruntfile.js, how to ignore node_modules from Git source control so it will be ready for build automation in further videos.
{: .prompt-tip }
{% include embed/youtube.html id='qk91C1WbPRA' %}

>If you would like to know more about this new developer service available on the [Azure](https://azure.microsoft.com/en-gb/) platform, you can have a look at the following post; [More about Azure DevTest Labs](https://mohamedradwan-devops.github.io/posts/more-about-azure-devtest-labs/). If you prefer a more concise description of the same feature, - [have a look at Quick overview of Azure DevTest Labs](https://mohamedradwan-devops.github.io/2016/06/29/quick-overview-of-azure-devtest-labs/).
{: .prompt-tip }

### Conclusion

ALM is a very broad term that reflects a change in attitude towards software development that is also expressed in the term DevOps. There are many ALM tools available for tracking application changes. These range from dedicated ALM products that monitor an application from inception to completion. Automatically sorting files into logical buckets as changes are noted. To simple wikis that require team members to record changes manually.

>If you would like to know more about Azure deployments, have a look at the post [How to deploy to Azure using Team Services Release Management](https://mohamedradwan-devops.github.io/posts/how-to-deploy-to-azure-using-team-services-release-management/). The post describes how Azure deployments are made easy by using Visual Studio Team Services (VSTS) Release Management. You will see a step-by-step tutorial on how to configure and deploy to Azure in Release Management. And moreover how to configure an end-to-end pipeline for deploying applications on Azure.

>You can see this video, if you would like to find more information about how to run JavaScript unit tests written in Jasmine using Visual Studio Test Explorer and Chutzpah extension, the main idea that this extension is a test adapter for Visual Studio so it helps Test Explorer to understand Jasmine JavaScript unit tests, it’s compatible with other JavaScript frameworks as well like Mocha and Qunit, using Chutzpah, we don’t need any Grunt or Gruntfile.js as this extension use Jasmine standalone version behind the scene.
{: .prompt-tip }
{% include embed/youtube.html id='gjRM-tTZwcw' %}