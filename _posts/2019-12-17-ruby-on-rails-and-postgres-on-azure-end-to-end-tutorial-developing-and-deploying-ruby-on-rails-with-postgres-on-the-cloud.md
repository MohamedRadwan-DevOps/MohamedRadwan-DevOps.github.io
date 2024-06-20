---
layout: post
title: "Ruby on Rails and Postgres on Azure End To End Tutorial | Developing and Deploying Ruby and Postgres"
date: 2019-12-17 12:45:53 +0100
---


## Overview

In this post, we will see how to build and deploy [Ruby on Rails](https://rubyonrails.org/)application using [Postgres](https://www.postgresql.org/)DB on [Azure App Service](https://azure.microsoft.com/en-gb/services/app-service/).

## Create Client Machines

The first step is to create the first Resource Group. The [Resource Group](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview)is a logical container in which Azure resources like Web App, VMs and Storage Account are deployed and managed. For example, you can choose to delete the entire Resource Group in one step later. 

So, in the first Resource Group, I will create 2 VMs, the main virtual machines that I will use in the demo. This will help you get a better understanding of how to configure and prepare your client machine to run Ruby on Rails and Postgres DB application.

![Ruby on Rails and Postgres on Azure End-To-End Tutorial](/assets/images/2019/12/Ruby-on-Rails-and-Postgres-on-Azure-End-To-End-Tutorial.gif)

## Install all the prerequisite

I will install all the prerequisites. The first is Git on the Windows machine, so I can connect to the Linux machine using SSH. Then, install Postgres and Ruby on Rails on the Linux machine that we connected to using SSH.

## Clone the sample application locally from GitHub

After that, we will use a sample application on GitHub. This sample application is a To-do list using Ruby on Rails and Postgres with basic CRUD (create, read, update, delete) operations. The first step is to clone this repo from GitHub to my local VM. Once I have done that, I will start installing some libraries for Ruby on Rails, then use bundler to restore the packages for the Ruby on Rails application. After that, build the application, migrate the Postgres DB locally on the local database, and then run the application.


>For more information about how to work with Kubernetes clusters and deploy them to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see **[Kubernetes cluster for beginners](%20https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/%20)**
{: .prompt-tip }

## Create Postgres Server on Azure

After that, I will create the main resource group that will have the rest of the resources for our lab. The first component is to create a Postgres Server on Azure. I will use a username and password which I will use later for configuring the connection string required to connect to the database. After that, I will create a firewall rule for Postgres on Azure. This is needed to be able to connect to the Postgres Server on Azure. 

Then, I will connect to the Postgres Server on Azure from the local Linux machine, and create a database. After that, I will create a deployment user, which is just a username and password that I will use later for pushing my application to the Azure App Service using Git commands.

## Create Azure Service Plan and Web App

After that, I will create an Azure service plan, which can be thought of as the infrastructure for the Web App. I will create the service plan with the basic pricing tier in a Linux container. 

Next, I will create the Web App based on the created App service plan. Part of this creation is Git deployment enabled, so I can push the application using Git commands.

## Set Azure App settings (Ruby on Rails environment variables for production)

After that, I will set some configurations in this Web App settings, using the username and password I created with the Postgres Server on Azure and the name of the Postgres Server.

## Push Ruby on Rails app to Azure

Finally, I will push my application to the Azure App service. Once I have pushed my application to the Azure App Service, this will run the Ruby on Rails migration, which will create the tables on the Postgres Server on Azure. Then, I can access the application, but this time from the Azure Web App. 

For more information about the rest of the steps, see the video...

### Commands

```bash
# Postgres
sudo apt-get update (update the repositories package URLs)
sudo apt install postgresql postgresql-contrib
sudo -u postgres psql \q
sudo -u postgres createuser mradwan (backup don\'t use it)
sudo -u postgres createuser -d mradwan
sudo -u postgres psql and then alter user mradwan createdb; \q

# Ruby on Rails
sudo apt install ruby-railties
git clone https://github.com/Azure-Samples/rubyrails-tasks.git
cd rubyrails-tasks
sudo apt install ruby-bundler (install the bundler package so I can call bundler command)
sudo gem update --system (update bundler version before running it)
sudo apt-get install libxslt-dev libxml2-dev zlib1g-dev (necessary required packages)
sudo apt install ruby-all-dev (necessary required packages)
sudo apt-get install libpq-dev (postgres client libs)
bundle install --path vendor/bundle (run bundler command)

# Run the app locally
rake db:create
rake db:migrate
rails server

# Azure
# Create a resource group
az group create --name RGLabRadwan --location "East US"

# Create Postgres DB
az postgres server create --location "East US" --resource-group RGLabRadwan --name postgrasradwanserver --admin-user userradwan --admin-password DevOpsAKS@1234 --sku-name GP_Gen5_2

# Postgres Firewall
az postgres server firewall-rule create --resource-group RGLabRadwan --server postgrasradwanserver --name AllowAllIps --start-ip-address 0.0.0.0 --end-ip-address 0.0.0.0

# Connect to Postgres Server
psql -U userradwan@postgrasradwanserver -h postgrasradwanserver.postgres.database.azure.com postgres
CREATE DATABASE sampledb;
CREATE USER radwanuserdb WITH PASSWORD 'DevOpsAKS@1234';
GRANT ALL PRIVILEGES ON DATABASE sampledb TO radwanuserdb;

# Connect local app to Azure Postgres
# change config/database.yml
production:
  <<: *default
  host: <%= ENV['DB_HOST'] %>
  database: <%= ENV['DB_DATABASE'] %>
  username: <%= ENV['DB_USERNAME'] %>
  password: <%= ENV['DB_PASSWORD'] %>

# Run from bash
export DB_HOST=postgrasradwanserver.postgres.database.azure.com
export DB_DATABASE=sampledb
export DB_USERNAME=userradwan@postgrasradwanserver
export DB_PASSWORD=DevOpsAKS@1234
rake db:migrate RAILS_ENV=production
rake assets:precompile
rails secret
export RAILS_MASTER_KEY= "generated secret"
export SECRET_KEY_BASE="generated secret"
export RAILS_SERVE_STATIC_FILES=true
rails server -e production

# Commit changes
git config --global user.email "mohamed@mohamedradwan.com"
git config --global user.name "mradwan"
git add .
git commit -m "database.yml updates"

# Deployment user
az webapp deployment user set --user-name userradwan --password DevOpsAKS@1234//!

# App service plan
az appservice plan create --name appserviceplancoreappradwan --resource-group RGLabRadwan2 --sku B1 --is-linux

# Web app
az webapp create --resource-group RGLabRadwan --plan appserviceplancoreappradwan --name appserviceappcoreradwan --runtime "RUBY|2.6.2" --deployment-local-git

# App setting connection string
az webapp config appsettings set --name appserviceappcoreradwan --resource-group RGLabRadwan --settings DB_HOST="postgrasradwanserver.postgres.database.azure.com" DB_DATABASE="sampledb" DB_USERNAME="userradwan@postgrasradwanserver" DB_PASSWORD="DevOpsAKS@1234"

# Run from bash
rails secret
az webapp config appsettings set --name appserviceappcoreradwan --resource-group RGLabRadwan --settings RAILS_MASTER_KEY="generated secret" SECRET_KEY_BASE="generated secret" RAILS_SERVE_STATIC_FILES="true" ASSETS_PRECOMPILE="true"

# Add git remote
git remote add azure https://userradwan@appserviceappcoreradwan.scm.azurewebsites.net:443/appserviceappcoreradwan.git
git push azure master

# Update model locally and redeploy
rails generate migration AddDoneToTasks Done:boolean
rake db:migrate
rails server
rake db:migrate RAILS_ENV=production

# Stream diagnostic logs
az webapp log config --name appserviceappcoreradwan --resource-group RGLabRadwan --docker-container-logging filesystem
az webapp log tail --name appserviceappcoreradwan --resource-group RGLabRadwan

# Delete RG
az group delete --name RGLabRadwan
```