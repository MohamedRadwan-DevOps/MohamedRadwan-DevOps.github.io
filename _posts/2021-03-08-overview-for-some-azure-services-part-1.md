---
layout: post
title: "Overview for some Azure Services (Part 1)"
date:   2021-03-08 11:46:07 +0100
---

## Event Hub

![Azure Event Hub](/assets/images/2021/03/Event-Hub.png)

### Characteristics

-   Big data event streaming service
-   To help in the process where you are continuously sending data to your service
-   Scalable up to terabytes of data and millions of events per second
-   Reliable with Zero data loss
-   Supports multiple protocols and SDKs

### Basics

-   Event producers
    -   Application and services that will send an event to [Event Hub](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-about)
-   Event Hub divided into partitions from 1 to 32, partitions are not changeable after creation
-   Event Hub namespace is the logical container you create in the portal to hold several Event Hubs and it has shared properties like throughput, access policy, cost, etc.
-   Pricing tier
    -   Basic, only gives you 1 consumer group
    -   Standard gives you 20 consumer groups
-   Throughput units
    -   From 1 to 20
    -   It indicates the performance of the Event Hub or how many messages you can process for the Event Hub.
    -   You can request to increase that up to 40 or create an **Event Hub** dedicated cluster.
-   Shared access policy on Event Hub namespace will be shared across all Event Hubs in this Event Hub namespace but shared access policy for Event Hub will be only for this Event Hub

### Sending Events

-   You can create a .Net app that uses Event Hub package or SDK so, you can send events (msgs) to Event Hub
-   You need to create an Access Policy with **Send** policy and use its connection string in the .Net app
-   You can use other services like Logic App, TSI to send Event to Event Hub

### Event Consumer

-   A consumer group is a unique view of Event Hub data
-   You can create a .Net app that uses **Event Hub** package or SDK so, you can get events (msgs) from Event Hub
-   You need to create an Access Policy with **Listen** policy and use its connection string in the .Net app
-   Offset is the position on Event Hub
-   A checkpoint is progress of saving offset on the client-side
-   In the .NET app you can use Storage Account so you can save the checkpoints

### Event Capture

-   Store the Event data on Azure storage more than the maximum retention policy duration (7 days)

## Databricks

![Azure Databricks](/assets/images/2021/03/Azure-Databricks2.png)

### Components

-   Workspaces
-   Shared
    -   Folder 1
    -   Folder 2
-   Users
    -   User A
        -   Folder 1
        -   Folder 2
    -   User B
        -   Folder 1
        -   Folder 2

Inside the folders, you usually put the Notebooks.

-   Workflows
    -   We can organize scripts to call other scripts inside what we call workflows

-   Clusters
    -   Cluster A
    -   Cluster B
    -   Cluster C

-   Jobs
    -   Job A
    -   Job B
    -   Job C

-   Experiment
    -   Experiment A
    -   Experiment B
    -   Experiment C

When you create an [Azure Databricks](https://azure.microsoft.com/en-gb/services/databricks/) cluster, there is a new resource group created that holds 2 VMs as nodes for your cluster, one is a master node that orchestrator other nodes, and the second is the worker node that does the job. Each Notebook divided into sections called cmds or cells you can run each cmd/cell separately.

## Azure Data Factory

![Azure Data Factory](/assets/images/2021/03/Azure-Data-Factory2.png)

Azure Data Factory is a cloud-based data integration service that allows creating workflows in the cloud for orchestrating and automating data movement and data transformation or ETL (Extracting, Transformation, and Loading). ADF does not store data. It just creates and designs workflows to orchestrate the movement of data between supported data stores and processing of data using compute.

### Components

-   Pipelines
-   Link Services
-   Datasets
-   IR (Integration Runtime)
-   Triggers
-   Monitor pipelines execution
