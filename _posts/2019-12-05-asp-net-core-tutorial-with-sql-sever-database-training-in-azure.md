---
layout: post
title: "ASP.NET Core and SQL Server Database Training in Azure App Service"
date: 2019-12-05 23:58:44 +0100
---

- [Overview of ASP.NET Core App with Entity Framework](#_Toc26481759)
- [Create Client Machine](#_Toc26481760)
- [Install all the prerequisites](#_Toc26481761)
- [Clone the sample application locally from GitHub](#_Toc26481762)
- [Create Azure SQL](#_Toc26481763)
- [Create Azure Service Plan and Web App](#_Toc26481764)
- [Set Azure App settings (Connection String and Env)](#_Toc26481765)
- [Push ASP.NET Core app to Azure](#_Toc26481766)

The following video has all the steps on how to do this tutorial:

{% include embed/youtube.html id='1QVRe7UHaro' %}


## Overview {#_Toc26481759}

In this post, we will see how to build and deploy an [ASP.NET Core](https://docs.microsoft.com/en-us/aspnet/core/?view=aspnetcore-3.1) application using Entity Framework Core with a [SQL Server database on Azure](https://azure.microsoft.com/en-gb/services/sql-database/#:~:targetText=Azure%20SQL%20Database%20is%20the,mission%2Dcritical%20SQL%20Server%20workloads.) App Service.

## Create Client Machine {#_Toc26481760}

The first step is to create the first Resource Group. The [Resource Group](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview) is a logical container in which Azure resources like Web App, VMs, and Storage Accounts are deployed and managed. For example, you can choose to delete the entire Resource Group in one step later. 

So, the first Resource Group I will create will contain the main virtual machine that I will use in the demo. This will help you get a better understanding of how to configure and prepare your client machine to run the ASP.NET Core application.

![ASP.NET-And-Entity-Framework-With-Azure](/assets/images/2019/12/ASP.NET-And-Entity-Framework-With-Azure.gif)

## Install all the prerequisites {#_Toc26481761}

I will install all the prerequisites. The first is Git, then the .NET Core SDK and runtime. If you just want to run the application, you can install the runtime, but since we are going to develop the ASP.NET Core application as well, we need the SDK. 

After that, I will install Visual Studio Code so I can edit and develop the application, and then install SQL Server Management Studio so I can connect later to the SQL Server on Azure.

## Clone the sample application locally from GitHub {#_Toc26481762}

We will use a sample application on GitHub. This sample application is a sample To-do list using ASP.NET Core and Entity Framework Core with basic CRUD (create, read, update, delete) functionality. The first step is to clone this repo from GitHub on my local VM. Once I do that, I will start restoring the packages and building the application, migrating the Entity Framework locally on the local database, and then running the application.

>For more information about how to work with Kubernetes clusters and deploy them to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see [Kubernetes cluster for beginner](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/)
{: .prompt-tip }

## Create Azure SQL {#_Toc26481763}

After that, I will create the main resource group that will have the rest of the resources for our lab. The first component is to create a logical SQL Server on Azure. I will use a username and password, which I will use later for configuring the connection string to connect to the database. After that, I will create firewall rules for SQL on Azure. This is needed to be able to connect to Azure SQL. 

Next, I will create an Azure database. The database will be created in the DTU model with an S0 basic tier. The DTU model is a database transaction unit which works well if you have pricing constraints and workload. It is also scalable if you want to upgrade it later in Azure database in the future. However, in the DTU model, CPU capabilities and storage capabilities are closely coupled. DTUs are a mix of CPU/IO and memory, so if you need more, you need to go for a different model. 

After that, I will create a deployment user, which is just a username and password that I will use later for pushing my application to the Azure App Service using Git commands.

## Create Azure Service Plan and Web App {#_Toc26481764}

Next, I will create an Azure service plan. Think of it as the infrastructure for the Web App. I will create the service plan with the basic pricing tier in a Linux container. After that, I will create the Web App based on the created App Service plan. Part of this creation process includes enabling Git deployment so I can push the application using Git commands.

## Set Azure App settings (Connection String and Env) {#_Toc26481765}

I will then set the connection string configuration in this Web App setting using the username and password I created with Azure SQL and use the name of the Azure SQL created. I will set the app settings configuration to be "Production" to hide any errors of Azure App Service from being displayed on the application. If I want to display the error in the Azure App Service, I must change the app setting to "Development" instead of "Production".

## Push ASP.NET Core app to Azure {#_Toc26481766}

To complete this ASP.NET Core Tutorial, I need to push my application to Azure App Service. Once I push my application to the Azure App Service, this will run the Entity Framework migration, which will create the database on SQL Server. Then I can access the application, but this time from the Azure Web App. For more info about the rest of the steps, see the video.

### Commands

```sh
# Clone the repository
git clone https://github.com/azure-samples/dotnetcore-sqldb-tutorial
cd dotnetcore-sqldb-tutorial
dotnet restore
dotnet ef database update
dotnet run

# Create a resource group
az group create --name RGLabRadwan --location "UK South"

# SQL Logical server
az sql server create --name sqlservercoreappradwan --resource-group RGLabRadwan --location "UK South" --admin-user userradwan --admin-password DevOpsAKS@1234

# Firewall rule
az sql server firewall-rule create --resource-group RGLabRadwan --server sqlservercoreappradwan --name FWRuleAllowAzureRadwan --start-ip-address 0.0.0.0 --end-ip-address 0.0.0.0

# SQL DB
az sql db create --resource-group RGLabRadwan --server sqlservercoreappradwan --name SQLDBcoreDBRadwan --service-objective S0

# Deployment user
az webapp deployment user set --user-name userradwan --password DevOpsAKS@1234

# App service plan
az appservice plan create --name appserviceplancoreappradwan --resource-group RGLabRadwan --sku B1 --is-linux

# Web app
az webapp create --resource-group RGLabRadwan --plan appserviceplancoreappradwan --name appserviceappcoreradwan --runtime "DOTNETCORE|2.2" --deployment-local-git

# Connection string
Server=tcp:sqlservercoreappradwan.database.windows.net,1433;Database=SQLDBcoreDBRadwan;User ID=userradwan;Password=DevOpsAKS@1234;Encrypt=true;Connection Timeout=30;

# Configure connection string
az webapp config connection-string set --resource-group RGLabRadwan --name appserviceappcoreradwan --settings MyDbConnection='Server=tcp:sqlservercoreappradwan.database.windows.net,1433;Database=SQLDBcoreDBRadwan;User ID=userradwan;Password=DevOpsAKS@1234;Encrypt=true;Connection Timeout=30;' --connection-string-type SQLServer

# Env var
az webapp config appsettings set --name appserviceappcoreradwan --resource-group RGLabRadwan --settings ASPNETCORE_ENVIRONMENT="Production"

# Git configuration
git config --global user.email "mohamed@mohamedradwan.com"
git config --global user.name "mradwan"

# Add git remote
git remote add azure https://userradwan@appserviceappcoreradwan.scm.azurewebsites.net/appserviceappcoreradwan.git
git push azure master

# Diagnostic Log
az webapp log config --name appserviceappcoreradwan --resource-group RGLabRadwan --docker-container-logging filesystem
az webapp log tail --name appserviceappcoreradwan --resource-group RGLabRadwan

# Delete RG
az group delete --name RGLabRadwan
```
