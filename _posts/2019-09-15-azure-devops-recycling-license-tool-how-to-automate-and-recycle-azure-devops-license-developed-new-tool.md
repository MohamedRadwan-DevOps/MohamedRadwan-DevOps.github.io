---
layout: post
title: "Azure DevOps Recycling License Tool | How To Automate and Recycle Azure DevOps License | Developed New Tool"
date: 2019-09-15 03:57:15 +0100
---

## Background and abstract

Managing Azure DevOps licenses within a global enterprise organization can be a real challenge. Typically, global organizations operate in many cities and different countries, with hundreds of projects and maybe hundreds of thousands of engineers who keep joining new projects or rolling off from existing projects every day. This often results in hundreds or thousands of Azure DevOps licenses that are no longer being used, and identifying and freeing them up or downgrading them can become a real challenge. Therefore, I developed a new tool, which is published on the Azure DevOps Marketplace, to solve all these problems and automate the process. 

The link for the tool on the Marketplace: [Azure DevOps Recycling License Tool](https://marketplace.visualstudio.com/items?itemName=MohamedRadwan-MVP.RecyclingLicense)

The following video explains in detail the challenges, how to install the prerequisites, and how to use the tool:

{% include embed/youtube.html id='Veu00o3Lnq8' %}

## The Challenge of Managing Azure DevOps for a Global Enterprise

As I explained before, managing Azure DevOps licenses within a global enterprise organization is a real challenge due to the nature of the global organization.

![The Challenge of Managing Azure DevOps for a Global Enterprise](/assets/img/2019/09/The-Challenge-of-Managing-Azure-DevOps-for-a-Global-Enterprise-1024x574.png)

## Intro About Azure DevOps Recycling License Tool

- Free up unused licenses based on configurable duration
- Downgrade Basic and Basic +Test Plan to Stakeholder based on configurable duration
- Several switches to enable and disable all options
- Dry run to validate and verify the actual action before it takes place
- Well descriptive logging into the screen as well as a file system

![Intro About Azure DevOps Recycling License Tool](/assets/img/2019/09/Intro-About-Azure-DevOps-Recycling-License-Tool-1024x572.png)

[Tip ( **[Kubernetes cluster for beginners](https://mohamedradwan-devops.github.io/2019/06/08/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/)** )]{.ion-tip}
For more information about how to work with Kubernetes clusters and deploy them to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see **[Kubernetes cluster for beginners](https://mohamedradwan-devops.github.io/2019/06/08/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/)**

## Integrating Recycling License Tool with Azure Pipeline for a Full Automation Process

We can integrate the Recycling License tool with Azure Pipeline using schedule triggers to have a fully automated process for freeing up, downgrading, or managing Azure DevOps licenses.

![Integrating Recycling License Tool With Azure Pipeline For a Full Automation Process](/assets/img/2019/09/Integrating-Recycling-License-Tool-With-Azure-Pipeline-For-a-Full-Automation-Process-1024x570.png)

## Installing the Prerequisites

- Install [Azure CLI](https://docs.microsoft.com/en-gb/cli/azure/install-azure-cli-windows?view=azure-cli-latest)
- Install [Azure DevOps extension](https://docs.microsoft.com/en-us/azure/devops/cli/get-started?view=azure-devops)

![Installing The Prerequisites for Recycling License Tool](/assets/img/2019/09/Installing-The-Prerequisites-for-Recycling-License-Tool-1024x581.png)

## Explaining the configuration file of the tool

```xml
<add key="dryRun" value="true" /> (dryRun) option, possible values {true or false}
```

This option is to validate all the processes before running the actual actions. This is the main switch to run the tool or just validate all actions. It's advisable to run at least one dry-run and verify the results to ensure they are as expected before running the actual run.

```xml
<add key="orgName" value="my org name" /> (orgName) option, possible values text with org name only
```

This option is the name of the Azure DevOps organization.

```xml
<add key="orgUrl" value="https://dev.azure.com/myorgname" /> (orgUrl) option, possible values text as URL
```
This option is the URL of the Azure DevOps organization.

```xml
<add key="personalaccesstoken" value="mo6rjfzh6g77gn6xu" /> (personalaccesstoken) option, possible values PAT value
```

This option is the access token that will be used to get the list of users with their information. It's advisable to use a token with minimum permissions like read without edit but on the organization level. The actual action like removing or downgrading a license will require you to log in with a proper account that has high permissions to change licenses or remove users from the organization.

```xml
<add key="enableDowngradeUserLicense" value="true" /> (enableDowngradeUserLicense) options, possible values {true or false}
```

This option is the duration in days required to downgrade licenses from Basic and Basic +Test Plans to Stakeholder if they are not active for that duration.

```xml
<add key="enableRemoveUserFromOrganization" value="true" /> (enableRemoveUserFromOrganization) option, possible values {true or false}
```

This option will enable or disable removing users from the Azure DevOps organization. By disabling this option with a false value, no action will be taken. Remember, if you enable this option by setting it to true with the dry run option set to true, this will show you how many users will be removed without actually removing them from the organization.

```xml
<add key="durationToRemoveUserFromOrganization" value="90" /> (durationToRemoveUserFromOrganization) option, possible values integer number
```
This option is the duration in days required to remove a user from the Azure DevOps organization if they are not active for that duration.

![Explaining The Configuration File of Recycling License for Azure DevOps](/assets/img/2019/09/Explaining-The-Configuration-File-of-Recycling-License-for-Azure-DevOps-1024x519.png)

## Run the tool in a dry-run mode for validation

It's very important to run the tool in a dry-run mode for the first time, then review and verify if the results and the logged information are as expected before running the actual mode. Note: Running the tool for the first time will create the configuration file.

![Run The Tool in a Dry-run Mode For Validation Recycling License](/assets/img/2019/09/Run-The-Tool-in-a-Dry-run-Mode-For-ValidationRecycling-License-1024x574.png)
## []{#_Toc19414042}Review the log file

You can review the log file for any dry-run or actual run.  

![Review the log file of Recycling License for Azure DevOps](/assets/img/2019/09/Reviewthe-log-file-of-Recycling-License-for-Azure-DevOps-1024x588.png)

## Login to Azure DevOps

Before you run the actual mode, you need to login to Azure DevOps with
an account that has privileges to downgrade license or remove users. You
will login using Azure CLI login command (AZ login)  

![Login to Azure DevOps organization](/assets/img/2019/09/Login-to-Azure-DevOps-organization-1024x364.png)

## Run the tool in an actual mode to real execute the actions

Once you logined and verified the result before in a dray-run, now you
ready to run the actual mode to make the tool takes real actions.

![Run The Tool in an Actual Mode To Real Execute The Actionsfor Azure DevOps Recycling License Tool](/assets/img/2019/09/Run-The-Tool-in-an-Actual-Mode-To-Real-Execute-The-Actionsfor-Azure-DevOps-Recycling-License-Tool-1024x579.png)

