---
layout: post
title: "How to Upload a Virtual Machine to the Cloud for Microsoft Azure"
date: 2015-09-21 22:43:45 +0100
---

Recently, I worked with [Microsoft Azure](https://azure.microsoft.com/en-us/) to provide better solutions using [Visual Studio 2015 and Team Foundation Server 2015](https://www.visualstudio.com/?Wt.mc_id=DX_MVP4039889) and [Visual Studio Online](https://www.visualstudio.com/?Wt.mc_id=DX_MVP4039889). Here I will just share my experience about that through a new series which introduce different and random features for [Microsoft Azure](https://azure.microsoft.com/en-us/).

1. [How to Upload a Virtual Machine to the Cloud for Microsoft Azure](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/)


## **How to Upload a Virtual Machine to the Cloud in Microsoft Azure**

[![YouTube Video](https://img.youtube.com/vi/1A6b2Gq4j58/0.jpg)](https://www.youtube.com/watch?v=1A6b2Gq4j58)

#### [Introduction](#introduction)

#### [1: Check-out the Container created in the Storage](#step1)

#### [2: Install Azure-PowerShell](#step2)

#### [3: Upload .Vhd File](#step3)

#### [4: Check-out uploaded .Vhd File in the Container](#step4)

#### [5: Create a Disk from a VHD](#step5)

#### [6: Create a New Virtual Machine using From Gallery Method](#step6)

#### [7: Connect to Windows Azure Virtual Machine](#step7)

#### [Conclusion](#conclusion)

## Introduction

This post will describe how to create and manage a **virtual machine** (**VM**) in **Microsoft Azure**. You will see step by step how to upload your local **virtual machine** to **Microsoft Azure Cloud** and create a fully functional **virtual machine** on the **cloud**.

>f you would like to learn more about using different environments during the realization of a software system, have a look at the post [Azure DevTest Labs Updates](https://mohamedradwan.com/posts/azure-devtest-labs-updates/). [Azure DevTest Labs](https://azure.microsoft.com/en-us/services/devtest-lab/) is a service provided by Microsoft Azure which provides functionality for managing environments that contain [Azure Virtual Machines](https://docs.microsoft.com/en-us/azure/virtual-machines/). The post mentioned above describes both the core capabilities of DevTest Labs and the new features of the service (as of February 2018).
{: .prompt-info }

## Step 1: Check-out the Container created in the Storage

In order to upload the **Virtual Machine**, you need to have a container inside the storage. If you don\'t have that already, you would need to create one.

1. From the navigation pane, click on **Storage**.
2. Click on the storage created \<**vmsmra**\> inside which you have created the container.
3. Click on the container created for your uploaded VHDs \<**uploadedvhds**\>.

[![Container created in the storage to upload virtual machine](/assets/images/2016/05/img001.jpg "1-Container created in the storage to upload virtual machine")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

> You can see this video if you would like to see how to create a Windows virtual machine on Azure. I will use a Windows 10 machine, connect remotely to it using remote desktop, install Docker for Windows in Linux mode, verify the Docker installation, fix errors, pull the docker hello-world image from Docker Hub, run a container from it, pull a SQL Express image, and nginx, run multiple containers from the same images, and verify it.
{: .prompt-info }
{% include embed/youtube.html id='W9ImzKuQGQ8' %}

## Step 2: Install Azure-PowerShell

You would need a machine to upload **.vhd file**. In this case, we will use **Azure PowerShell**. If you don\'t have **Azure PowerShell**, you will need to download it.

1. Use the direct link to download the **.msi** file for **Azure-PowerShell**: [Download](https://go.microsoft.com/fwlink/?LinkID=279888&clcid=0x409).
   **Note**: You can also download it from [GitHub](https://github.com/Azure/azure-powershell).
2. Click on the downloaded **.msi file** to install **Azure-PowerShell**.
3. Click on the **License Agreement** check box.
4. Click on **Install**.

[![Install Azure Powershell (machine) to upload vhd file](/assets/images/2016/02/2-install-azure-powershell-machine-to-upload-vhd-file_thumb.jpg "2-Install Azure Powershell (machine) to upload vhd file")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

>If you would like to know more about Azure deployments, have a look at the post [How to deploy to Azure using Team Services Release Management](https://mohamedradwan.com/posts/how-to-deploy-to-azure-using-team-services-release-management/). 
The post describes how Azure deployments are made easy by using Visual Studio Team Services (VSTS) Release Management. You will see a step-by-step tutorial on how to configure and deploy to Azure in Release Management, and how to configure an end-to-end pipeline for deploying applications on Azure.
{: .prompt-tip }

## Step 3: Upload .Vhd File

When you upload **.vhd file**, you can place it anywhere within your blob storage.

1. Run **Microsoft Azure PowerShell**.
2. The **PowerShell console** will open up. Type `**Add-AzureAccount**` and press enter. 
   **Note**: Type `**help azure**` to get all the cmdlets.
3. You will be prompted to sign in to your Microsoft account. Type your email address and password then press enter.

[![Upload vhd file by running microsoft azure powershell](/assets/images/2016/02/3-upload-vhd-file-by-running-microsoft-azure-powershell_thumb.jpg "3-Upload vhd file by running microsoft azure powershell")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

>You can see this video if you would like to find more information about how to create a Linux machine on Azure. We will select an Ubuntu server, remote connect to it using Git Bash and PuTTY, and test our connection using the sudo command.
{: .prompt-info }
{% include embed/youtube.html id='C0ecnvmdAuQ' %}

4. Type a command with the following syntax and press enter: 
   `**Add-AzureVhd -Destination <url> -LocalFilePath <FileInfo>**` 
   Where: 
   - **Add-AzureVhd** cmdlet allows you to upload on-premises virtual hard disks (in .vhd file format) to a blob storage account as fixed virtual hard disks.
   - **-Destination <url>** specifies the URL of a blob in Blob Storage. The parameter supports SAS URL, although patching scenarios destination cannot be an SAS URL.
   - **-LocalFilePath <FileInfo>** specifies the path to the local .vhd file.

   In our case, we will type: 
   `**Add-AzureVhd -Destination https://vmsmra.blob.core.windows.net/uploadedvhds/vsalm.vhd -LocalFilePath "E:VisualStudio2013 Update3 ALMWMIv2Virtual Hard Disks2012R2Eval.vhd"**`

[![Upload vhd file by running microsoft azure powershell (2)](/assets/images/2016/02/4-upload-vhd-file-by-running-microsoft-azure-powershell-2_thumb.jpg "4-Upload vhd file by running microsoft azure powershell (2)")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

>If you would like to know more about this new developer service available on the [Azure](https://azure.microsoft.com/en-gb/) platform, you can have a look at the following post: [More about Azure DevTest Labs](https://mohamedradwan.com/posts/more-about-azure-devtest-labs/). If you prefer a more concise description of the same feature, [have a look at Quick overview of Azure DevTest Labs](https://mohamedradwan.com/posts/quick-overview-of-azure-devtest-labs/).
{: .prompt-info }

5. It would calculate **MD5 Hash**, **detect empty blocks**, and then **upload the vhd file**. The total elapsed time can be around **1.5 hours**, depending on your internet speed and the size of the VHD.

[![Upload vhd file by running microsoft azure powershell (3)](/assets/images/2016/02/5-upload-vhd-file-by-running-microsoft-azure-powershell-3_thumb.jpg "5-Upload vhd file by running microsoft azure powershell (3)")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

>If you would like to learn more about using the [Build Variables](https://docs.microsoft.com/en-us/vsts/build-release/concepts/definitions/build/variables?tabs=batch) in [VSTS](https://www.visualstudio.com/team-services/) and Release Management, have a look at the following post: [VSTS Build variables and Echo](https://mohamedradwan.com/posts/vsts-build-variables-and-echo/). The post describes how to see the output at any point of time while automating a process, through setting variables and displaying them during the build.
{: .prompt-tip }

## Step 4: Check-out uploaded .Vhd File in the Container

The uploaded **.vhd file** would be saved in the designated container inside the storage.

1. From the navigation pane, click on **Storage**.
2. Click on the storage \<**vmsmra**\>.
3. Click on the container \<**uploadedvhds**\> to view uploaded VHDs.
4. You can now view your uploaded vhd \<**vsalm.vhd**\>.

[![Uploaded vhd in the container](/assets/images/2016/02/6-uploaded-vhd-in-the-container_thumb.jpg "6-Uploaded vhd in the container")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

> You can see this video if you would like to find more information about the story behind containers and what drives the need for them. We will understand why companies moved from traditional solution architecture to Microservices and how containers are the perfect solution for running them. We will clear some definitions, tools, and keywords related to this ecosystem. We will understand the difference between VM, Container, and Hyper-V Container, and why we would prefer container over VM. We will also understand the difference between container and image, the lifecycle of creating a new image, adding more layers to the base image, and pushing that to a container images registry on the cloud, then pulling that from the registry to anywhere to have a new container. We will understand different technologies and services around containers, like Docker, Docker Swarm, Kubernetes, Azure Container Services (ACS), and Azure Container Registry. We will see how to create a Linux machine on Azure, remote connect to it using Git Bash and PuTTY, how to install Docker, display all the images that exist on the machine, pull new images from Docker Hub, run and stop containers, and display running containers. We will also see the same steps on Windows with Docker.
{: .prompt-info }
{% include embed/youtube.html id='X13AdWYC2KI' %}

## Step 5: Create a Disk from a VHD

After you transfer the **.vhd file** from your local machine to the container in **Microsoft Azure**, you must create a **disk**.

1. From the **Azure classic portal**, under **All Items**, click on **Virtual Machines**.
2. Under **Virtual Machines**, click on **Disks**.
3. From the command bar at the bottom of the Portal screen, click on **Create**.
4. A pop-up window \<**Create a disk from a VHD**\> will be displayed. In the **Name** field, type a unique disk name. In this case, we have named it **VSALMDisk**.
5. In the **VHD URL** field, click on the folder icon.

[![Create a disk from vhd from Azure classic portal](/assets/images/2016/02/7-create-a-disk-from-vhd-from-azure-classic-portal_thumb.jpg "7-Create a disk from vhd from Azure classic portal")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

>If you are interested in developing a [Visual Studio Team Service extension](https://docs.microsoft.com/en-us/vsts/extend/overview), and you would like to know and follow the best practices for DevOps, Continuous Integration, and Continuous Delivery, have a look at the following post: [Develop VSTS Extension and Configure CI (Continuous Integration) and CD (Continuous Delivery Pipeline)](https://mohamedradwan.com/posts/develop-vsts-extension-and-configure-ci-continuous-integration-and-cd-continuous-delivery-pipeline/).
{: .prompt-info }

6. Browse to the container location. Click on **vmsmra**.
7. From the containers within **vmsmra**, click on **uploadedvhds**.
8. Click on the uploaded vhd \<**vsalm.vhd**\>.
9. Click on **Open**.

[![Create a disk from vhd from Azure classic portal (2)](/assets/images/2016/02/8-create-a-disk-from-vhd-from-azure-classic-portal-2_thumb.jpg "8-Create a disk from vhd from Azure classic portal (2)")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

> You can see this video if you would like to find more information about an introduction and overview of a series of videos about Microsoft Dynamics development, including the overview of the Microsoft Dynamics CRM itself, installing Microsoft Dynamics 2016 on Azure VM and how to upgrade to Dynamics 365, how to develop Dynamics CRM plugin, how to debug Microsoft Dynamics CRM project, create and run unit tests using FakeXRMEasy and Microsoft Fakes, JavaScript and front-end unit tests, as well as code quality using JSHint, also how to create and run UI, and how to integrate all the practices as part of the CI/CD (Continuous Integration and Continuous Delivery).
{: .prompt-info }

{% include embed/youtube.html id='rEJMBwuKY6Y' %}

10. Click on **The VHD contains an operating system** check box.
   **Note**: In **Operating System Family**, select your **OS**. In this case, we will select **Windows**.
11. Click on the checkmark.

[![Create a disk from vhd from Azure classic portal (3)](/assets/images/2016/02/9-create-a-disk-from-vhd-from-azure-classic-portal-3_thumb.jpg "9-Create a disk from vhd from Azure classic portal (3)")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

12. After a few minutes, it will show a notification that the **disk has been successfully created**.
13. You can then see the disk created \<**VSALMDisk**\> in the list of disks.

[![Create a disk from vhd from Azure classic portal (4)](/assets/images/2016/02/10-create-a-disk-from-vhd-from-azure-classic-portal-4_thumb.jpg "10-Create a disk from vhd from Azure classic portal (4)")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

> You can find more information about **DevOps** in the following post: [DevOps: The Three Stage Conversation - People, Process, Products](https://mohamedradwan.com/2016/10/31/devops-the-three-stage-conversation-people-process-products/) which describes the basic principles of **DevOps**. This post will be especially helpful to those for whom DevOps is still a new concept. If you prefer a deeper view on this topic, have a look at the following guide: [Quick guide about Basic Principles of DevOps](https://mohamedradwan.com/2017/11/03/published-a-quick-guide-about-basic-principles-of-devops/), which presents an overview of the [DevOps](https://www.visualstudio.com/vs/devops/) process and practices, describing "the big picture," while still maintaining a high level of detail.
{: .prompt-info }

## Step 6: Create a New Virtual Machine using From Gallery Method

The **Microsoft Azure Portal** provides two basic methods to create a new **virtual machine**: **Quick Create** and **From Gallery**. In this case, we will use the **From Gallery Method**.

1. Under **Virtual Machines**, click on **Instances**.
2. From the command bar at the bottom of the Portal screen, click on **New**.
3. A pop-up window will open up. Under **Virtual Machine** options, click on **From Gallery**.

[![Create virtual machine from microsoft azure portal](/assets/images/2016/02/11-create-virtual-machine-from-microsoft-azure-portal_thumb.jpg "11-Create virtual machine from microsoft azure portal")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

4. On the **Choose an Image** page, click on **My Disks**.
5. Click on the disk you created \<**VSALMDisk**\>.
6. Click on the proceed arrow icon.

[![Create virtual machine from microsoft azure portal and choose an image](/assets/images/2016/02/12-create-virtual-machine-from-microsoft-azure-portal-and-choose-an-image_thumb.jpg "12-Create virtual machine from microsoft azure portal and choose an image")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

>You can see this video if you would like to find more information about how to install Microsoft Dynamics CRM 365 on Azure VM. Presented installation using SQL 2014 and SQL 2016, on several versions of Windows Server (Windows Server 2012, Windows Server 2012 R2, and Windows Server 2016). Installing Domain Controller, explained all possible issues, which you may face during the installation, like incompatible Domain Controller Windows Server 2012 with SQL Server on the same machine, Windows Search Service is not started automatically, installing Dynamics CRM reporting extension, which was needed to create an additional Dynamics Organization and many other notes.
{: .prompt-info }

{% include embed/youtube.html id='EGpw9fI-gIY' %}

7. On the first **Virtual Machine Configuration** page, specify the name for the **virtual machine** in the **Virtual Machine Name** field. In this case, we have used **VSALM-mra**.
   **Note**: In the **Tier** field, make sure **Standard** is selected.
8. Under the **Size** field, select **D2 (2 cores, 7 GB memory)**.
9. Click on the proceed arrow icon.

[![Create virtual machine from microsoft azure portal and set virtual machine configuration](/assets/images/2016/02/13-create-virtual-machine-from-microsoft-azure-portal-and-set-virtual-machine-configuration_thumb.jpg "13-Create virtual machine from microsoft azure portal and set virtual machine configuration")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

10. On the second **Virtual Machine Configuration** page, set the following **virtual machine** attributes:
   - **Cloud Service** - This is a cloud service container for virtual machines that you create. You can create a new cloud service container for a single virtual machine or place multiple virtual machines in the same cloud service for load balancing.
   - **Cloud Service DNS Name** - This is the global DNS name that is used to contact the virtual machine.
   - **Region/Affinity Group/Virtual Network** - This is the Region where you want the virtual machine resources to be physically deployed. The Affinity Group attribute allows Azure to keep all services in a group physically close. The Virtual Network attribute allows you to define the network to connect to the virtual machine.
   - **Availability Set** - This is used to define a group of virtual machines that are deployed across fault and update domains.
   - **Endpoints** - These are the communication ports through which the virtual machine can be contacted.

11. Click on the proceed arrow icon.

[![Create virtual machine from microsoft azure portal and set virtual machine configuration (2)](/assets/images/2016/02/14-create-virtual-machine-from-microsoft-azure-portal-and-set-virtual-machine-configuration-2_thumb.jpg "14-Create virtual machine from microsoft azure portal and set virtual machine configuration (2)")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

>In some of the posts, you can find high-level descriptions of [Agile](https://mohamedradwan.com/2017/07/08/quick-intro-to-agile/) principles and the usage of some [Agile tools](https://mohamedradwan.com/2017/07/16/tfs-2015-agile-project-management/) and [Agile methodology](http://agilemanifesto.org/).
{: .prompt-info }

12. On the third **Virtual Machine Configuration** page, set the following **virtual machine** attributes:
   - **VM Agent** - The VM Agent installs extensions that enhance the interaction with the virtual machine. This option cannot be disabled when installing a Linux image. For Windows data disks and Linux images and disks, a version of the VM agent that supports extensions must already be installed in the operating system.
   - **Configuration Extensions** - These are extensions that enhance the management of the virtual machine, including the execution of custom scripts.
   - **Security Extensions** - These are extensions that enhance the security of the virtual machine, such as antivirus support.

13. Click on the checkmark.

[![Create virtual machine from microsoft azure portal and set virtual machine configuration](/assets/images/2016/02/15-create-virtual-machine-from-microsoft-azure-portal-and-set-virtual-machine-configuration_thumb.jpg "15-Create virtual machine from microsoft azure portal and set virtual machine configuration")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

14. You can see near the command bar at the bottom left of the Portal screen, the **Virtual Machine being created**. It will first **create the virtual machine**, **provision the virtual machine**, and then **install extensions in the virtual machine**.
15. After a few minutes, it will show a notification that the **virtual machine has been successfully started.**
16. You can then see the new **virtual machine** created \<**VSALM-mra**\> in the list of **VM Instances**.

[![Create virtual machine from microsoft azure portal (2)](/assets/images/2016/02/16-create-virtual-machine-from-microsoft-azure-portal-2_thumb.jpg "16-Create virtual machine from microsoft azure portal (2)")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

> this video if you would like to find more information about my personal experience of the migration Team Foundation Server to Visual Studio Team Services using Database Import Service or TFS Migrator tool provided by Visual Studio Team. Going through all six phases of the migration, following the migration guide provided by Microsoft as a walkthrough. You will see how to get started with the migration process and which prerequisites should be completed. The most important prerequisite is that you must have Azure Active Directory in order to use TFS Migrator tool. See more about the two different process models supported by VSTS, Inherited and Hosted XML. See which decisions you should make and how to validate them, for example, which customizations you should keep and which one to remove. To prepare the first collection dacpac, first you should prepare Azure Storage Container, create a dacpac file and afterwards upload it. To prepare the second collection Azure VM, you should install SQL Server, backup the DB from the collection and upload it to the Azure storage container. See first how to import (dry - run) and how to change the configuration afterwards in order to import (production).
{: .prompt-info }

{% include embed/youtube.html id='7C6LG6k4wcU' %}

## Step 7: Connect to Windows Azure Virtual Machine

In the **Azure classic portal**, you use the **Connect button** to start a **Remote Desktop session** and log on to a **Windows VM**.

1. From the navigation pane, click on **Virtual Machines**.
2. Under **Virtual Machines**, click on the name of the **virtual machine** \<**VSALM-mra**\>.
3. From the command bar at the bottom of the Portal screen, click on **Connect**.
4. Click on **OK**. It creates and downloads a **Remote Desktop Protocol file (.rdp file)**.

[![Connect to windows azure virtual machine by downloading rdp file](/assets/images/2016/02/17-connect-to-windows-azure-virtual-machine-by-downloading-rdp-file_thumb.jpg "17-Connect to windows azure virtual machine by downloading rdp file")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

> The post [Upgrade to TFS 2018 Has Been Done in Production](https://mohamedradwan.com/2018/01/16/upgrade-to-tfs-2018-has-been-done-in-production/) describes a full upgrade and migration from TFS2015 to TFS2018 and describes the improvements over the old TFS 2015.
{: .prompt-info }


5. Open the downloaded **.rdp file** from your local machine.
6. In the **Windows Security** window, type the credentials for an account on the **virtual machine**.
7. Click on **OK**.

[![Connect to windows azure virtual machine by downloading rdp file (2)](/assets/images/2016/02/18-connect-to-windows-azure-virtual-machine-by-downloading-rdp-file-2_thumb.jpg "18-Connect to windows azure virtual machine by downloading rdp file (2)")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

8. You can now access the machine of **Brian Keller** that you uploaded in **Windows Azure**.

[![Connect to Brian Keller windows azure virtual machine](/assets/images/2016/02/19-connect-to-brian-keller-windows-azure-virtual-machine_thumb.jpg "19-Connect to Brian Keller windows azure virtual machine")](https://mohamedradwan.com/posts/how-to-upload-a-virtual-machine-to-the-cloud-for-microsoft-azure/#main)

>You can see this video if you would like to find more information about how to get started with Release Management and its advantages. See how to create a build definition using CI/CD Tools for VSTS Extensions (I will be using Package Extension and Publish Artifact tasks), and also using **DevOps-VSTS-POC** trigger in order to enable CI. All of that is in order to be able to publish, share, install and query versions. You will see how to create a release definition, choose an artifact and configure the source for the artifact and default version. See how to create different environments or clone the existing one. In my case, I am going to create QA, Preproduction, and Production environments, each with one phase and one task. See also how to configure the Publish Extension task for each environment. See an end-to-end continuous delivery pipeline using VSTS extension with Build and Release Management.
{: .prompt-info }

{% include embed/youtube.html id='uGAcWLnSU0A' %}

## Conclusion

The **Microsoft Azure Portal** provides multiple, simple methods to create and manage **virtual machines** in the **Microsoft public cloud**. Using the **Quick Create method**, you can quickly create new **virtual machines** and go back later to set more configuration options. Using the **From Gallery method**, you can fully customize the **virtual machine configuration** before it is deployed into the physical region as a standalone or load-balanced service.

**Microsoft Azure virtual machines** scale in processor memory and storage, allowing you to create **virtual machines** with a large number of cores and memory, and data disks up to **1 TB in size**. As an added benefit, you can easily move a **virtual machine** created in **Microsoft Azure** to **Hyper-V** and back since both use the same virtualized hardware and VHD format. This allows you to quickly reconfigure services on-premise or redeploy to the public cloud to adjust to changing business conditions.

>In one of the old posts [TFS 2015 Agile Project Management](https://mohamedradwan.com/2017/07/16/tfs-2015-agile-project-management/), you can read more about new [**Agile Project Management**](https://docs.microsoft.com/en-us/vsts/work/backlogs/overview) features in **TFS 2015**, which provide better support for aligning across teams while giving autonomy to individual teams; you can use the same structure with VSTS/TFS2018.
{: .prompt-tip }
