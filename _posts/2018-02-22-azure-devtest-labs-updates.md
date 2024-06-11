---
layout: post
title: "Azure DevTest Labs Updates"
date: 2018-02-22 01:08:45 +0100
---

## Introduction

All [DevOps](https://mohamedradwan.com/posts/what-is-devops/) teams need different kinds of environments during the realization of a software system. The availability of environments is of great importance for the speed of delivering that piece of value for the business. [**Azure DevTest Labs**](https://mohamedradwan.com/posts/quick-overview-of-azure-devtest-labs/) is a service provided by [**Microsoft Azure**](https://azure.microsoft.com/en-us/) which allows managing environments that contain [**Azure Virtual Machines**](https://docs.microsoft.com/en-us/azure/virtual-machines/). It helps developers and testers to quickly create environments in **Azure** while minimizing waste and controlling cost. Developers can also use artifacts to quickly deploy and configure applications. By using custom images and formulas, developers can save virtual machines (VMs) as templates and easily reproduce them across the team. **DevTest Labs** also offers several configurable policies that lab administrators can use to reduce waste and manage a team's environments.

>If you would like to know more about this new developer service available on the [Azure](https://azure.microsoft.com/en-gb/) platform, you can have a look at the following post: [More about Azure DevTest Labs](https://mohamedradwan.com/posts/more-about-azure-devtest-labs/). If you prefer a more concise description of the same feature, have a look at [Quick overview of Azure DevTest Labs](https://mohamedradwan.com/posts/quick-overview-of-azure-devtest-labs/).
{: .prompt-tip }


## Scenarios

**Azure DevTest Labs** is a solution for fast, easy, and agile dev-test environments in Azure. **Azure DevTest Labs** can be used to implement many key scenarios:

- For developers (to host development machines) - developers can quickly provision their development machines on demand and customize them whenever needed.
- Test environments (to host machines for testers) - testers can test the latest version of their application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.
- Training/education - create a lab where you can provide custom templates that each trainee can use to create identical and isolated environments for training.

## Core capabilities of DevTest Labs

A lab is the infrastructure that encompasses a group of resources, such as Virtual Machines (VMs). It is created from the [**Azure Marketplace**](https://azuremarketplace.microsoft.com/en-us/marketplace/). Azure VMs give you the flexibility of virtualization, although you still need to maintain the VM by performing certain tasks such as configuring, patching, and installing the software that runs on it. Once created, you can:

1. Connect to the VM
2. Start
3. Stop
4. Delete
5. [Apply artifacts](https://mohamedradwan.com/posts/creating-virtual-machines-with-artifacts-in-devtest-labs/)

![1 - Core capabilities of DevTest Labs](https://mohamedradwan.com/posts/azure-devtest-labs-updates/1-core-capabilities-of-devtest-labs/)

You can also manage configuration and policies: allowed virtual machine sizes, virtual machines per user, virtual machines per lab, auto shutdown, auto start, manage repositories, marketplace images or custom images, and also you can monitor the cost.

>You can see this video, if you would like to find more information about Visual Studio Code, which is part of the Visual Studio family. The marketplace for the supported extensions is demonstrated, as well as the process of installing, disabling, and reloading the extensions, and starting a new project - a new console application - and debugging this new project.
{: .prompt-tip }
{% include embed/youtube.html id='GWdGSsUxkHE' %}

## New Features of DevTest Labs

- Managed Disks Support - now Azure DevTest Labs supports Managed Disks in all labs, including VM OS disks, data disks, and custom images. Managed Disks help you manage multiple storage accounts for a large number of VMs. All managed-disk resources are automatically managed by Azure instead of your own storage accounts, which simplifies scalable VM deployments and management.

  ![2 - Managed Disks support](https://mohamedradwan.com/posts/azure-devtest-labs-updates/2-managed-disks-support/)

- Claimable VMs - lab admins can prepare VMs and put them in a shared pool, and lab users can pick a working VM from the pool whenever they need one.

  ![3 - Claimable VMs](https://mohamedradwan.com/posts/azure-devtest-labs-updates/3-claimable-vms/)

- Create identical VMs in a batch - now you can create multiple identical VMs in Azure DevTest Labs from the same VM image and artifacts all at once. You just need to provide a number of the VM instances.

  ![4 - Create identical VMs in a batch](https://mohamedradwan.com/posts/azure-devtest-labs-updates/4-create-identical-vms-in-a-batch/)

- VM auto expiration - you can set an expiration date by specifying a date on which the VM automatically will be deleted.

  ![5 - VM auto-expiration](https://mohamedradwan.com/posts/azure-devtest-labs-updates/5-vm-auto-expiration/)

- Minimize public IP addresses - Azure DevTest Labs lets lab VMs share the same public IP address in order to minimize the number of public IP addresses required to access your individual lab VMs.

  ![6 - Minimize public IP addresses](https://mohamedradwan.com/posts/azure-devtest-labs-updates/6-minimize-piblic-ip-addresses/)

## Conclusion

**Azure DevTest Labs** is an Azure service that lets you quickly create environments in Azure while minimizing waste and controlling costs. **DevTest Labs** is useful any time you require dev or test environments, and want to reproduce them quickly or manage them by using cost-saving policies. **DevTest Labs** provides many benefits in creating, configuring, and managing developer and test environments in the cloud.
