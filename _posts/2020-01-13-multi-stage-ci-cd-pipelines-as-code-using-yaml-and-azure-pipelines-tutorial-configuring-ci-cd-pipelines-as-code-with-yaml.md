---
layout: post
title: "Multi-stage CI/CD pipelines as code using YAML and Azure Pipelines Tutorial | Configuring CI/CD Pipelines as Code with YAML"
date:   2020-01-13 23:24:48 +0100
---

The following video has all the steps on how to do this tutorial:  

{% include embed/youtube.html id='i77vEEVAfB8' %}

## Intro

You will see a complete tutorial on how to create and configure CI/CD pipelines as code using the [YAML](https://yaml.org/) configuration language. Also, how to build a multi-stage pipeline which means that we have more than one stage in the same YAML file. We can have build stage, integration test stage, deployment stage, and many more as needed.

Be aware that this tutorial will not cover any infrastructure as code. There are other tutorials on my blog that will do that, like the one with [Ansible](https://mohamedradwan-devops.github.io/posts/using-ansible-to-automate-infrastructure-deployment-to-azure-using-ansible-and-azure-pipelines/) and the one with [Terraform](https://mohamedradwan-devops.github.io/posts/deploying-infrastructure-automatically-to-the-cloud-using-terraform-and-azure-pipelines-tutorial/).

In this tutorial, I will use a sample project on GitHub named Pars-Unlimited that is developed in ASP.NET Core.

[![Pipelines-as-YAML](/assets/img/2020/01/Pipelines-as-YAML.gif)](https://mohamedradwan-devops.github.io/posts/multi-stage-ci-cd-pipelines-as-code-using-yaml-and-azure-pipelines-tutorial-configuring-ci-cd-pipelines-as-code-with-yaml/pipelines-as-yaml/)

## Creating the infrastructure for the application manually

So, the first step is to start creating the infrastructure for the application manually, since we are not doing it as code. To do that, I will open my Azure portal and create a resource group. I will use a predefined Azure template which will create all the components needed for the infrastructure for the application. This includes an [Azure Service Plan](https://azure.microsoft.com/en-gb/pricing/details/app-service/plans/), Azure Web App, and SQL Server on Azure. Also, the template will create and configure an Azure firewall rule for Azure SQL, so Azure Web App can have permission to access Azure SQL.

> For more information about how to work with Kubernetes cluster and deploy it to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see **[Kubernetes cluster for beginner](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/)**
{: .prompt-tip }

## Create a YAML pipeline file

Once I complete that, I will open Azure DevOps and navigate to the Azure pipeline. The first step is to create a YAML pipeline file which is the build pipeline as code, then choose the location where I want to store the file. The YAML file is usually stored in the same repository with the application code. When I create the YAML file, I can choose which YAML template to use. Since my application is an ASP.NET application, I will choose the ASP.NET template, which is a ready-made YAML file for some build tasks for ASP.NET. The template tasks include restoring all the NuGet packages, building the application, running the unit tests, and so on.

## Run or kick a continuous integration build

After that, I will run or kick a continuous integration build.

## Adding a new pipeline stage to the YAML file

After the build completes, I will open the YAML file again for editing. I will add a new step to start creating the web package.zip, then store that package on Azure DevOps artifacts, then run or kick a new build again. Once the build is complete, I will start editing the YAML file again, then adding a new stage. To create a new stage, I will do that by copying the old stage and renaming it from build to deployment. Then in the deployment stage, I will start adding some new tasks to pick up the web package and deploy that package to the Azure Web App. During the deployment stage, the pipeline will download the web package on the pipeline agent, then deploy that package to the [Azure Web App](https://azure.microsoft.com/en-gb/services/app-service/web/). After that, I will change the connection string of the web app using the connection string from the web.config in my application to make sure that it will be translated correctly.

## Browse the application after deploying it to Azure

Then browse the application from the Azure Web App to see the application.

The following is the final YAML file content:

```yaml
# ASP.NET
# Build and test ASP.NET projects
# Add steps that publish symbols, save build artifacts, deploy, and more:
# https://docs.microsoft.com/azure/devops/pipelines/apps/aspnet/build-aspnet-4
trigger:
  - master
stages:
  - stage: Build
    jobs:
      - job: Build
        pool:
          vmImage: 'vs2017-win2016'
        variables:
          solution: '**/*.sln'
          buildPlatform: 'Any CPU'
          buildConfiguration: 'Release'
        steps:
          - task: NuGetToolInstaller@1
          - task: NuGetCommand@2
            inputs:
              restoreSolution: '$(solution)'
          - task: VSBuild@1
            inputs:
              solution: '$(solution)'
              msbuildArgs: '/p:DeployOnBuild=true /p:WebPublishMethod=Package /p:PackageAsSingleFile=true /p:SkipInvalidConfigurations=true /p:PackageLocation="$(build.artifactStagingDirectory)"'
              platform: '$(buildPlatform)'
              configuration: '$(buildConfiguration)'
          - task: VSTest@2
            inputs:
              platform: '$(buildPlatform)'
              configuration: '$(buildConfiguration)'
          - task: PublishBuildArtifacts@1
            inputs:
              PathtoPublish: '$(Build.ArtifactStagingDirectory)'
              ArtifactName: 'drop'
              publishLocation: 'Container'
  - stage: Deploy
    jobs:
      - job: Deploy
        pool:
          vmImage: 'vs2017-win2016'
        steps:
          - task: DownloadBuildArtifacts@0
            inputs:
              buildType: 'current'
              downloadType: 'single'
              artifactName: 'drop'
              downloadPath: '$(System.ArtifactsDirectory)'
          - task: CmdLine@2
            inputs:
              script: |
                echo Tell me all folders and file in this path
                dir /b /s
          - task: AzureRmWebAppDeployment@4
            inputs:
              ConnectionType: 'AzureRM'
              azureSubscription: 'Visual Studio Enterprise(ff1d424e-36cd-400a-ba00-d801cb0bf0a4)'
              appType: 'webApp'
              WebAppName: 'WebAppSQLRadwan'
              packageForLinux: '$(System.ArtifactsDirectory)/drop/*.zip'
```