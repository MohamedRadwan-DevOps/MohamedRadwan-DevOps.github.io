---
layout: post
title: "Overview of Service Endpoints"
date:   2016-08-08 14:11:54 +0100
---

### Introduction 

The **Endpoint** represents the **URL** from where your service can be accessed by a client application. You can also visit [**Visual Studio website**](https://www.visualstudio.com/en-us/docs/integrate/extensions/develop/service-endpoints) and go through the tutorial that will show how to develop a **Service Endpoint** by creating an example **Extension** for **Team Services**. You can create a service endpoint in [**Configuration**](https://msdn.microsoft.com/en-us/library/ms734786(v=vs.110).aspx) as well as in [**Code**](https://msdn.microsoft.com/en-us/library/ms731080(v=vs.110).aspx). The extensible platform and tools that work with **VSTS Endpoint** is quite long and it\'s presented in the next image. The connections including Jenkins, HipChat, Slack, Zendesk and much more. The image below presents only some of the connections, but please note that this is not the finalized list of all connections. Some of the partners are not represented here as they are using some of the other services for integrations, such as [**Service Hooks**](https://www.visualstudio.com/da-dk/docs/integrate/api/hooks/overview). Service Endpoints are usually integrated in the area for pulling or pushing Artifact which are related to **[Build Release](https://www.visualstudio.com/en-us/features/release-management-vs.aspx)**. So **Service Endpoints** are representing one way to connect [**VSTS**](https://mohamedradwan-devops.github.io/posts/license-types-for-visual-studio/) to another product, but it can be also connected in a different, more appropriate way if this is necessary, depending on what are the needs for connection. 

![0-VSTS Integrations and Marketplace](/assets/images/2016/08/0-VSTS-Integrations-and-Marketplace.jpg "0-VSTS Integrations and Marketplace")

>You can see this video, If you would like to see how to create Windows virtual machine on Azure. I will use Windows 10 machine, connect remotely to it using remote desktop. Installing Docker for windows in Linux mode. I will see how to verify that Docker installation succeeded and fix some errors. And also pull docker hello-world image from Docker-Hub and running a container from it and also pull a SQL Express image as well as nginx. And run many containers from the same images and see how we can verify that and many others.
{: .prompt-tip }
{% include embed/youtube.html id='W9ImzKuQGQ8' %}

>Read detailed explanation about all types of **Scrum and Agile meetings** (Sprint Planning, Stand-up, Grooming, [Sprint Review](https://docs.microsoft.com/en-us/vsts/work/scrum/sprint-planning), Retrospective Meeting) in my past post [Types of meetings in Scrum and Agile](https://mohamedradwan-devops.github.io/posts/types-of-meetings-in-scrum-and-agile/).
{: .prompt-tip }


### What is Service Endpoint 

**Service endpoints** are enabling **Team Services** to connect to external systems or services. They are set of features, securely stored by **Team Services** which includes also: Service Name, Description, Server URL, Certificates or Tokens, User names and passwords. **Extensions** can then leverage the **Service Endpoint** to obtain stored data to perform the necessary operations in that service. The image below represents basically the **Service Endpoints** user interface. 

![Service Endpoint User Interface](/assets/images/2016/08/Service-Endpoint-User-Interface.jpg "Service Endpoint User Interface")

>Read about basic guidelines that you need to consider when building a **product backlog** in the following post, [Requirements (Epic, Feature, User Story), Task Size and Estimation in Agile and Scrum](https://mohamedradwan-devops.github.io/posts/requirements-epic-feature-user-story-task-size-and-estimation-in-agile-and-scrum/), and also about its maintaining and refinement of product backlog in [Key tips for Maintaining good product backlog in Agile and Scrum](https://mohamedradwan-devops.github.io/posts/key-tips-for-maintaining-good-product-backlog-in-agile-and-scrum/).
{: .prompt-tip }


>In one of the old posts [TFS 2015 Agile Project Management](https://mohamedradwan-devops.github.io/posts/tfs-2015-agile-project-management/) you can read more about new [**Agile Project Management**](https://docs.microsoft.com/en-us/vsts/work/backlogs/overview) features in **TFS 2015,** which provide better support for aligning across teams, while giving autonomy to individual teams; you can use the same structure with VSTS/TFS2018.
{: .prompt-info }

How we actually create them - there is an admin experience that allows you to often decide what **service endpoints** you need to create. It will then prompt with a dialog box and you can fill the pertinent information and then we can establish the connection between **VSTS** and the third party or the external system that we want to connect to and then throughout our **Build** and [**Releases**](https://mohamedradwan-devops.github.io/posts/difference-between-continuous-deployment-and-release-management/) we are then able to identify this is the **service endpoint** that I need to use to get [**Artifact**](https://mohamedradwan-devops.github.io/posts/create-your-author-custom-artifacts-in-devtest-labs/), to get that information from that external system. When creating **Service Endpoint** for **Azure**, there is possibility to create a **Service Endpoint** for **Azure.** You can create it using **Credentials**, **Certificate** or **Service Principal**. The difference between all three ways, is that some of the tasks inside of task library work only with one type of authentication. Generally for creating **Service Endpoint** for **Azure**, you will need two types of **Authentication**. It is highly recommendable to create **Service Principal** or **Credentials** authentication and also create **Certificate** credentials, because in this way you will be able to reach all different [Assets](https://azure.microsoft.com/en-us/documentation/articles/automation-credentials/) in [Azure](https://azure.microsoft.com/en-us/?b=16.24).

### Conclusion

**Endpoints** are defined by stating an address, a binding, and a contract. Other parameters that can be set at the **endpoint configuration** include the behaviour, headers and listen **URIs**. For some specific types of **endpoints** these values don\'t change. Such example is metadata exchange endpoints, which is always using the **IMetadataExchange contract**. Other endpoints, such as **\<T:System.ServiceModel.Web.WebHttpEndpoint\>** always require a specified **endpoint** behaviour.

>You can see this video, f you would like to find more information about an introduction and overview of a series of videos. About enhancing Frontend development code quality. It includes understanding different types of JavaScript unit testing frameworks like Jasmine. Mocha, Jest, different types of task runner like Grunt and Gulp. Different types of linting tools, like JSHint, ESLint, JSLint, CSSLint, different types of code formatter like Prettier and Tidy. How to write your first JavaScript using test with Jasmine standalone version.
{: .prompt-info }
{% include embed/youtube.html id='sOptXMvePqE' %}

Also How to run JavaScript unit tests using Grunt, Command Line and PhantomJS . How to calculate code coverage for JavaScript unit tests using Istanbul. and to run JavaScript unit tests using Visual Studio Test Explorer using chutzpah extension. Also to linting JavaScript code using JSHint and how to run that from Command Line using Grunt. Finally it shows how to integrate all the quality practices with Visual Studio Team Service Build automation so it can be part of CI/CD. Or Continuous Integration and Continuous Delivery.

>If you are in a situation when you need to integrate two backlogs, read the step-by-step post about [Two Backlog Integration](https://mohamedradwan-devops.github.io/posts/trello-vsts-integration/) in which I am providing a detailed description of the integration between [**Trello**](https://trello.com/) and [**VSTS**](https://www.visualstudio.com/team-services/) using [Zapier](https://zapier.com/).
{: .prompt-tip }
