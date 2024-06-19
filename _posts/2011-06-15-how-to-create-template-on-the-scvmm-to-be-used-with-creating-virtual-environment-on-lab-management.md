---
layout: post
title: "How to create template on the SCVMM to be used with creating virtual environment on Lab Management?"
date:   2011-06-15 18:36:09 +0100
---

[Updated on April 17, 2012]You can see the full video series (93 videos) of install and configure TFS 2010 in enterprise, see the guide on the Codeplex <http://tfs10enterprise.codeplex.com/> [End of April 17, 2012 update]{style="color:#0000ff;"}

First of all, you can create the template with an auto tool which exists at the following links: <http://archive.msdn.microsoft.com/vslabmgmt> <http://vslabmgmt.codeplex.com/>

But I prefer to describe the manual process so we can understand what happens there. So, what are the steps?

- Install OS, SP, and any needed components.
- Install the Test Agent (and don\'t configure).
- Install the Lab Agent (no configuration needed).
- Install the Build Agent (and don\'t configure).
- Because I didn\'t use DHCP in my domain, I make a static IP for the DNS on the virtual machine. This IP points to my domain so when I create a new environment, I can join the domain automatically while creating the environment.
- I also enable the Win 2008 R2 feature (.NET Framework 3.5) because the Build Agent will need it.
- I fix the date and time because Egypt now changed the summer time, no longer change.

After I create the environment, I make the following, just for reminding:

- Configure Test Agent for client machine as an interactive process with **TFSLAB** account.
- Add **TFSBUILD** account to the Administrators local group account for any virtual machine that will have build.
- Configure Build Agent using **TFSBUILD** account ([no longer needed, see this post] [click here](https://mohamedradwan-devops.github.io/2011/06/17/complete-the-virtual-machine-after-you-create-your-environment/ "After create your environment")).
