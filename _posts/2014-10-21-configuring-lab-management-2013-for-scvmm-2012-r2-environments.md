---
layout: post
title: "Configuring Lab Management 2013 for SCVMM 2012 R2 Environments"
date: 2014-10-21 21:35:02 +0100
---

In this post, I will explain with videos how to configure Lab Management 2013 with SCVMM 2012 R2 so we can create and manage SCVMM environments in Team Foundation Server 2013. For more information, visit the MSDN [Configuring Lab Management for SCVMM Environments](http://msdn.microsoft.com/en-us/library/dd380687.aspx "Configuring Lab Management for SCVMM Environments").

The following are the steps:

1. Installing HV and verifying it is working properly
2. Improving the reliability of WinRM
3. Installing SCVMM 2012 R2 prerequisites
4. Creating 2 folders: SCVMM Library and SCVMM VMs
5. Installing SCVMM 2012 R2
6. Adding Hyper-V Host to SCVMM 2012 R2
7. Installing SCVMM Admin Console on TFS machine
8. Configuring Lab Management for Team Foundation Server
9. Installing and configuring Test Controller
10. Verifying Lab Management and Test Controller configured successfully
11. Note-1: Stopping and starting WinRM with SCVMM
12. Note-2: Fix SPN that VMM requires were not correctly registered

### 1. Installing Hyper-V and verifying it is working properly

{% include embed/youtube.html id='W0dtglCtYLw' %}

### 2. Improving the reliability of WinRM

See how to increase the **maxtimeoutms** for Windows Remote Management, which is required for Lab Management.

{% include embed/youtube.html id='BhB4H6nSF2c' %}

### 3. Installing SCVMM 2012 R2 prerequisites

See how to install System Center Virtual Machine Manager 2012 R2 prerequisites.

{% include embed/youtube.html id='VE1CF_h0bs0' %}

### 4. Creating 2 folders: SCVMM Library and SCVMM VMs

Creating one folder for the Library share that will hold templates and VMs and another folder for the deployed VMs.

{% include embed/youtube.html id='WMcjLjMhOXA' %}

### 5. Installing SCVMM 2012 R2

{% include embed/youtube.html id='_oglaiiVkcc' %}

### 6. Adding Hyper-V Host to SCVMM 2012 R2

{% include embed/youtube.html id='qumcAy1vx2M' %}

### 7. Installing SCVMM Admin Console on TFS machine

{% include embed/youtube.html id='29cUZwYvK6o' %}

### 8. Configuring Lab Management for Team Foundation Server

{% include embed/youtube.html id='aWWxH5O3Pbg' %}

### 9. Installing and configuring Test Controller

{% include embed/youtube.html id='KAOdgWP067o' %}

### 10. Verifying Lab Management and Test Controller configured successfully

{% include embed/youtube.html id='ri7Z4CPEcm4' %}

### 11. Note-1: Stopping and starting WinRM with SCVMM

In case you want to stop and start Windows Remote Management with System Center Virtual Machine Manager installed, you will have to stop the System Center Virtual Machine Management Agent and start it manually.

{% include embed/youtube.html id='wjs5bTPcIPY' %}

### 12. Note-2: Fix SPN that VMM requires were not correctly registered

See the following video if you encounter the following error: 

**The Service Principal Names (SPNs) that VMM requires were not correctly registered when the VMM management server**

{% include embed/youtube.html id='LXYhVVLLM78' %}

