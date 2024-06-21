---
layout: post
title: "VSTS Build variables, Echo and arguments"
date: 2018-03-11 14:27:07 +0100
---

Seeing the output at any point in time is very important while automating a process; for that reason we usually set variables and display them during the build. In [**VSTS**](https://www.visualstudio.com/team-services/), the public variables can be defined in the **Variables** tab or in the running process. Knowing and seeing the value of **Environment** variables is part of the issue described above and is, therefore, also very important. The following links provide the lists of [**Build Variables**](https://docs.microsoft.com/en-us/vsts/build-release/concepts/definitions/build/variables?tabs=batch) and [**Build definition source repositories**](https://docs.microsoft.com/en-gb/vsts/build-release/concepts/definitions/build/repository).

>For more information about how to work with Kubernetes cluster and deploy it to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see [**Kubernetes cluster for beginner**](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/).
{: .prompt-tip }

The process of setting and displaying a variable is described in more detail below. First, I create a **Command Line** task to write my name, so I can recognize that part very quickly.


![Creating a Command Line task in VSTS](/assets/img/2018/03/Creating-a-Command-Line-task-in-VSTS-1024x555.png)

Then I create the second **Command Line** task to print out the value. Remember the variable is **\$(var)**, but since we use that with echo, we will use **%var%**.

![VSTS Command Line task - print out the value of a variable](/assets/img/2018/03/VSTS-Command-Line-task-print-out-the-value-of-a-variable-1024x572.png)

> Variable names are transformed to uppercase, and the characters "." and " " are replaced by "_".
>
> For example, **Agent.WorkFolder** becomes **AGENT_WORKFOLDER**. On **Windows**, you access this as **%AGENT_WORKFOLDER%** or **\$env:AGENT_WORKFOLDER**. On **Linux** and **macOS** you use **\$AGENT_WORKFOLDER**.

In **Ubuntu**, it doesn’t include the full path with the drive letter like **Windows**.

![Define and modify your variables Azure DevOps on Linux and macOS](/assets/img/2018/03/Define-and-modify-your-variables-Azure-DevOps-on-Linux-and-macOS-1024x624.png)

But I can use the relative path to package my files from the working directory as the following. In the following example, Yarn creates a folder inside the working directory called "**Build**" and puts in it all the files for the package. Then I will zip it and store it on **Azure DevOps** Artifacts store.

![Archive the build from Azure DevOps on Ubuntu and Linux](/assets/img/2018/03/Archive-the-build-from-Azure-DevOps-on-Ubuntu-and-Linux-1024x398.png)

>If you would like to learn more about using the [Build Variables](https://docs.microsoft.com/en-us/vsts/build-release/concepts/definitions/build/variables?tabs=batch) in [VSTS](https://www.visualstudio.com/team-services/) and Release Management, also [working with variables](https://docs.microsoft.com/en-us/azure/devops/pipelines/process/variables?view=vsts&tabs=yaml%2Cbatch), have a look at the following post: [VSTS Build variables and Echo](https://mohamedradwan-devops.github.io/posts/vsts-build-variables-and-echo/). The post describes how to see the output at any point in time while automating a process, through setting variables and displaying them during the build.
{: .prompt-tip }

>For more information about how to work with **Docker**, like pulling a docker image, running a docker image, and working with a container, see [**Docker for beginners**](https://mohamedradwan-devops.github.io/posts/docker-for-beginners-step-by-step-tutorial/).
{: .prompt-tip }

The following image demonstrates how the values are displayed:

![VSTS - displaying the value of a variable during the Build](/assets/img/2018/03/VSTS-displaying-the-value-of-a-variable-during-the-Build.png)

>If you would like to know more about Azure deployments, have a look at the post [How to deploy to Azure using Team Services Release Management](https://mohamedradwan-devops.github.io/posts/how-to-deploy-to-azure-using-team-services-release-management/). The post describes how Azure deployments are made easy by using Visual Studio Team Services (VSTS) Release Management. You will see a step-by-step tutorial on how to configure and deploy to Azure in Release Management, and moreover, how to configure an end-to-end pipeline for deploying applications on Azure.
{: .prompt-tip }


### How to send arguments to PowerShell and read them during VSTS Build

[Read more about sending arguments to PowerShell and reading them during VSTS Build](https://docs.microsoft.com/en-us/vsts/build-release/tasks/utility/powershell?view=vsts).

The PowerShell script will contain write-host with argument numbers:

![VSTS Build PowerShell expose argument values](/assets/img/2018/03/VSTS-Build-PowerShell-expose-argument-values.png)

In the PowerShell task, we send the arguments by putting each argument in double quotes with a space separator:

![Send arguments to VSTS Build PowerShell script](/assets/img/2018/03/Send-arguments-to-VSTS-Build-PowerShell-script-1024x542.png)

### When we run the build, it will look like the following

![Rung VSTS Build to see the arguments sent to the PowerShell script](/assets/img/2018/03/Rung-VSTS-Build-to-see-the-arguments-sent-to-the-PowerShell-script.png)

### Use Build variables and send them as arguments to PowerShell task which runs the PowerShell script

[Read more about setting variables in scripts](https://docs.microsoft.com/en-us/vsts/build-release/concepts/definitions/build/variables?view=vsts&tabs=batch#set-in-script). Using the previous example, we will set 2 variables. Also, I made one of them secret as it holds the password:

![Set VSTS Build variables](/assets/img/2018/03/Set-VSTS-Build-variables.png)

Now, I can use them as arguments by sending each variable in double quotes with \$(var) and a space separator:

![Send VSTS Build variables as arguments to PowerShell VSTS Build task](/assets/img/2018/03/Send-VSTS-Build-variables-as-arguments-to-PowerShell-VSTS-Build-task-1024x685.png)

>For more information about how to work with **Git** with animation. All commands will be represented in graphical animation. E.g. git branch, git merge, git rebase, git cherry-pick and many others, see [**Mastering Git with animation**](https://mohamedradwan-devops.github.io/posts/mastering-git-from-beginner-to-advanced-step-by-step-with-graphical-animation-commands/).
{: .prompt-tip }

### When I run the build, this will display the arguments variables as the following:

![How VSTS Build variables will be displayed as arguments sent to the PowerShell task script](/assets/img/2018/03/How-VSTS-Build-variables-will-be-displayed-as-arguments-sent-to-the-PowerShell-task-script.png)

### Access the VSTS Build variables without sending PowerShell arguments

[Stack Overflow good related question/answer](https://stackoverflow.com/questions/36997494/vsts-pass-build-variables-into-powershell-script-task?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa) I don’t have to send PowerShell arguments as I can access my variables that I set in the VSTS build. The access here is by calling them in the PowerShell script. For example, in our scenario, I set the variable **domain.username**. To access it within the script, I need to transfer "." to "_" so I have to call it as **\$env:domain_username**.

![Calling VSTS build variable within PowerShell](/assets/img/2018/03/Calling-VSTS-build-variable-within-PowerShell.png)
