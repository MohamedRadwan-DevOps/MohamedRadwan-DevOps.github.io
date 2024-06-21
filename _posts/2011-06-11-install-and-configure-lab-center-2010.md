---
layout: post
title: "Install and configure Lab Center 2010"
date:   2011-06-11 18:40:44 +0100
---

[Updated on April 17, 2012] You can see the full video series (93 videos) of install and configure TFS 2010 in enterprise, see the guide on the Codeplex [here](https://github.com/DevOpsFounder/TFS-2010-Enterprise-Installation-and-Configuration-Video-Guide) [End of update April 17, 2012 update]

Prepare your environment as follows:

- Lab Management with TFS architecture

![Lab-Management-Architecture](/assets/img/2011/06/Lab-Management-Architecture-1024x361.jpg)

- Install TFS, Build Server, and Test Controller

![TFS-Without-LabManagement](/assets/img/2011/06/TFS-Without-LabManagement.jpg)

- Install Hyper-V on a physical machine
- Install SCVMM on the Hyper-V machine or any other machine
- Install Admin console on the SCVMM machine to configure the library and add the host machine(s) (Hyper-V) to the SCVMM
- Install Admin console on the TFS machine
- Configure Lab Management on the TFS machine from the TFS Administration console

![TFS-With-LabManagement](/assets/img/2011/06/TFS-With-LabManagement.jpg)

- Create virtual machines on the Hyper-V and prepare them as you need (one Windows 2008 R2, one Windows 7, one Windows Vista, etc.)
- Join all created virtual machines to the domain
- Install Lab Agent, Test Agent, Build Agent on every virtual machine (as needed). For example, if you will not run automated tests on the virtual machine you will not need a test agent
- Run those machines on the Hyper-V so you can create the template from them
- Create templates using the existing configured virtual machine that is running on the Hyper-V, or if you didn\'t run them in the Hyper-V, you can create them from virtual hard disk (VHD) and then put those templates on the library
- Import the templates in the Lab Management from the library
- Create any number of environments using imported virtual machines (templates)
- Deploy the created environment to Hyper-V (it happens automatically as you create your environment)
- You can store the environment on the library or not
- Start using your environment in your manual or automated tests

### Notes

- I decided to install the build controller on the TFS and create a separate machine as a build server which has the build agent. I will also create a separate machine as a test controller because the recommendation is to not install the test controller on the TFS machine and also not install the build agent on the TFS machine.
- Hyper-V will be the host for all virtual machines in my infrastructure including TFS, Build Server, Test Controller machines. It will also include the library of the templates, actual virtual machines, or environments, and the running environment. Remember, the library can have template machines or virtual environments. In other words, you can create the template from a virtual machine and store it in the library, and you can also create a virtual environment and store it in the library on the SCVMM.
- When you install the build agent on the virtual machine, at the last step choose option 3 (Manual configure or use with Lab Management) and when you click configure from the Lab Center, it will configure it automatically.
- After you create the virtual machine that you will use to create your templates, if any error occurs while setting up the build agent, try adding the account needed to the administrators group of the virtual machine itself.
- When I configure Lab Management from TFS Admin Console at the project collection configuration, at service account settings, I chose **TFSLAB** which is a domain account with restricted permission. This account will be used when I configure the **Test Agent** on the virtual machine that has the Test Agent, and also will be used by the Lab Management to configure the Build Agent.
- After you install Test Agent, you configure it to run as a service or interactive process (Coded UI test).
- You install the Test Agent if you want to run automated tests on the machine and you may configure it as **Service** if it\'s a server machine (web server for example) or configure as **Interactive process** if it\'s a client machine (Windows 7 for example). If you log in in the interactive case, you must log in using **TFSLAB** or the account that was used to configure Test Agent and Lab Management configuration on TFS Admin console.
- Test Agent configured manually on the virtual machine: start -> Test Agent configuration.
- Build Agent configured automatically by the Lab Management on the virtual machine: when connecting to the machine using Lab center, click configure button.
- When I configure Test Agent with the **TFSLAB** account, I have an error: "Test agent is not configured to run interactively under this account. Run the Test Agent Configuration Tool to change the interactive user account." This error could happen for many reasons. My reason was that I wrote the domain when configuring the Test Agent like (mydomain.com\TFSLAB) but it should be (Mydomain\TFSLAB). Another reason could be if you configure the Test Agent using a local account. For more info see the following link [Troubleshooting errors in lab management](http://blogs.msdn.com/b/lab_management/archive/2009/10/26/troubleshooting.aspx?ocid=soc-n-eg-elite--MRadwan " Troubleshooting errors in lab management")

![TestAgent](/assets/img/2011/06/TestAgent.png)
![TestAgent2](/assets/img/2011/06/TestAgent2.png)
