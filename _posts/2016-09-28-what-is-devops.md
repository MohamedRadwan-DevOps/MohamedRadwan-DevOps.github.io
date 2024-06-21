---
layout: post
title: "What is DevOps"
date: 2016-09-28 19:54:17 +0100
---


### Introduction 

In one of my previous posts, I briefly described the main ideas behind [**DevOps**](https://mohamedradwan-devops.github.io/posts/devops-framework-and-practices/). **DevOps** is about improving the collaboration between the traditionally siloed **development** and **operations** functions. **DevOps** is all about trust, communication, and merging of two different disciplines inside IT. On one side we have **developers**, and on the other side, we have **operations**. **DevOps** is an extension of [**Agile**](http://agilemanifesto.org/) software development principles - allowing us to build, deploy, and change our software with accelerated delivery cycle times.

To learn more about Agile Software Testing, have a look at the [quick guide about Agile Software Testing](https://mohamedradwan-devops.github.io/posts/published-a-quick-guide-about-agile-software-testing/). This guide presents the basic idea behind Agile methodology and its connection to software testing. It describes the structural idea of Agile and explains the importance of adaptation to changes in the fast-paced software development world.

The post [Upgrade to TFS 2018 Has Been Done in Production](https://mohamedradwan-devops.github.io/posts/upgrade-to-tfs-2018-has-been-done-in-production/) describes a full upgrade and migration from TFS2015 to TFS2018 and details the improvements over the old TFS 2015.

## What is DevOps

Traditional **Development** and **Operations** teams worked in a way that the **Development team** created a solution for production. When it was finished, they handed it over to the **Operations team**. The **Operations team** then started preparing to implement the project in the production environment and manually changed the configuration files and other data to comply for deployment. This caused a lot of duplication and issues which were very hard to resolve due to different files and environments.

![1-traditional-development-and-operations](/assets/img/2016/09/Traditional-Development-and-Operations.jpg "1-traditional-development-and-operations")

[**DevOps**](https://www.microsoft.com/en/server-cloud/solutions/development-operations.aspx) is a software development method that stresses communication, collaboration, and integration between software developers and information technology (IT) professionals. It enables the rapid evolution of products and services, lowers risk, enhances quality across portfolios, and reduces costs.

**DevOps** integration targets product delivery, quality testing, feature development, and maintenance releases to improve reliability, security, and faster development and deployment cycles. The adoption of **DevOps** is motivated by the following factors:

- Use of **Agile** and other development operations
- Requirement for an expanded rate of production releases from application and business stakeholders
- Extensive possibility of visualized and cloud infrastructure from internal and external providers
- Increased usage of data center automation and configuration management tools

### Principles of DevOps

One commonly cited [**DevOps principle**](https://www.microsoft.com/en-us/cloud-platform/development-operations) is "Infrastructure as a code". Another major principle is to get fast feedback throughout every phase of the software lifecycle. Feedback helps to achieve a higher quality of code and to reduce bugs in production. Moreover, [**DevOps practices**](https://www.microsoft.com/en/server-cloud/solutions/development-operations.aspx) help gather data to identify, diagnose, and resolve issues quickly.

- Develop and test in an environment similar to production
- Frequent build deployment
- Continuous validation of operation quality
- Strengthen feedback loops


>You can see [**this video**](https://www.youtube.com/watch?v=ekFaRprcmWo&t=24s), if you would like to find more information about how to scan JavaScript code for better code quality enhancements and suggestions using Static Code Analysis or Linting tools. In this video, we will see how to use JSHint, how to download the grunt-contrib-jshint npm package. We will also see how to change the Gruntfile.js configuration to include JSHint settings and run that from the Command Line and Visual Studio Command Task Runner.

>If you are interested in developing a [Visual Studio Team Service extension](https://docs.microsoft.com/en-us/vsts/extend/overview), and you would like to know and follow the best practices for DevOps, Continuous Integration, and Continuous Delivery, have a look at the post [Develop VSTS Extension and Configure CI (Continuous Integration) and CD (Continuous Delivery Pipeline)](https://mohamedradwan-devops.github.io/2017/12/29/develop-vsts-extension-and-configure-ci-continuous-integration-and-cd-continuous-delivery-pipeline/).

### Why DevOps Exist 

There is a gap between **Developers** and the **Operations** team. With the implementation of **DevOps**:

- Close collaboration between Developers and Operations to understand the impact of code changes.
- Developers work in an environment that is very close to the production environment.
- Developers are focused on metrics required by the Ops team.
- More transparency for Operations on infrastructure needs.
- Higher level of automation in deployment.
- The pipeline of Dev - Test - Prod is closely monitored for each deployment with immediate feedback.
- Better collaboration and communication.

![2-what-is-devops](/assets/img/2016/09/What-is-DevOps-1.jpg "2-what-is-devops")


>For cases demanding high fidelity migration for work-items, the post [TFS 2017 Migration To VSTS with VSTS Sync Migrator](https://mohamedradwan-devops.github.io/2017/09/15/tfs-2017-migration-to-vsts-with-vsts-sync-migrator/) describes the migration without any limitations for migrating links, attachments, or work items.

>You can see this video, if you would like to find more information about an introduction and overview of a series of videos about Microsoft Dynamics development. Including the overview of Microsoft Dynamics CRM itself, installing Microsoft Dynamics 2016 on Azure VM and how to upgrade to Dynamics 365. How to develop Dynamics CRM plugin, how to debug Microsoft Dynamics CRM project, create and run unit tests using FakeXRMEasy and Microsoft Fakes, JavaScript and front end unit tests as well as code quality using JSHint. Also, how to create and run UI and how to integrate all the practices as part of CI/CD (Continuous Integration and Continuous Delivery).
{: .prompt-tip }

{% include embed/youtube.html id='rEJMBwuKY6Y' %}

### Conclusion

**DevOps** is helping businesses in a tremendous way. It bridges the gap between Developers' **'need for change'** and Operations' **'resist to change'**, creating a smooth path for continuous development and continuous integration. If you are interested in taking a **DevOps Self-Assessment**, you can visit **[Microsoft's website](http://devopsassessment.azurewebsites.net/)** and gauge your readiness in the **7 key DevOps practice areas**.

>If your migration process only requires migrating the work items, with no need to migrate links & relations between them, you can consider using the TFS Integration Platform, which is less complicated than the VSTS Sync Migrator. For more information about this tool, visit [TFS 2017 Migration To VSTS with TFS Integration Platform](https://mohamedradwan-devops.github.io/posts/tfs-2017-migration-to-vsts-with-tfs-integration-platform/).
{: .prompt-tip }


>If you would like to learn more about using different environments during the realization of a software system, have a look at the post [Azure DevTest Labs Updates](https://mohamedradwan-devops.github.io/2018/02/22/azure-devtest-labs-updates/). [Azure DevTest Labs](https://azure.microsoft.com/en-us/services/devtest-lab/) is a service provided by Microsoft Azure which provides functionality for managing environments that contain [Azure Virtual Machines](https://docs.microsoft.com/en-us/azure/virtual-machines/). The post mentioned above describes both the core capabilities of DevTest Labs and the new features of the service (as of February, 2018).
{: .prompt-info }

