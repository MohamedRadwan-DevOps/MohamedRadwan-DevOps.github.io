---
layout: post
title: "Migrating Team Foundation Server to Visual Studio Team Services using Database Import Service TFS Migrator"
date:   2018-04-09 00:34:00 +0100
---

## Introduction

In this post, I am going to share my personal experience of the
Migration [Team Foundation Server](https://www.visualstudio.com/tfs/) to
[Visual Studio Team
Services](https://www.visualstudio.com/team-services/) using Database
Import Service or TFS Migrator. The TFS Database Import Service, also
known shorthand as the Import Service, provides a high fidelity way to
migrate collection databases from TFS to VSTS. If you are looking to use
this service to import your collection(s), there is a migration guide
provided by Microsoft which I strongly recommend to use it during your
migration as a walkthrough (you can download it from the following
[link](https://aka.ms/TFSDataImport)). There are six phases of the
migration timeline shown in the following image. We will go through all
of them.

![Six phases of the Migration process of TFS to VSTS](/assets/images/2018/03/Six-phases-of-the-Migration-process-of-TFS-to-VSTS.jpg "Six phases of the Migration process of TFS to VSTS")

## 1.Get started

In this step, let us first understand why we want to migrate from Team
Foundation Server to Visual Studio Team Services.

## 2.Prerequisites

-   The main task for this second step is to make sure that we have a
    working [Azure Active
    Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-whatis)
    that will be used for authenticating the team members in our VSTS
    account.
-   We cannot migrate to an existing VSTS account since the tool is
    creating a new one. In case you want to migrate to an existing
    account, you cannot use this tool.
-   VSTS support two different process models:
    -   [Inherited](https://docs.microsoft.com/en-us/vsts/work/customize/inheritance-process-model?view=vsts)
        (default model)
    -   [Hosted
        XML](https://docs.microsoft.com/en-us/vsts/work/customize/hosted-xml-process-model?view=vsts)
        (by default is turned off)
-   Each Team Project Collection will be mapped to separate VSTS
    account, for which later Microsoft will provide an entity where we
    can keep multiple VSTS accounts.
-   Always download the latest version of TFS Migrator Tool

>If you can\'t migrate using TFS Migrator and your
migration demanding high fidelity for work-item, the post [TFS 2017
Migration To VSTS with VSTS Sync
Migrator](https://mohamedradwan-devops.github.io/posts/tfs-2017-migration-to-vsts-with-vsts-sync-migrator/)
describes the migration without any limitations for migrating links,
attachments
{: .prompt-tip}



>If your migration process only requires migrating the
work items, with no need to migrate links & relations between them, you
can consider using the TFS Integration Platform, which is less
complicated than the VSTS Sync Migrator. For more information about this
tool, visit [TFS 2017 Migration To VSTS with TFS Integration
Platform](https://mohamedradwan-devops.github.io/posts/tfs-2017-migration-to-vsts-with-tfs-integration-platform/).
{: .prompt-tip}

## 3.Upgrade TFS to the latest version

-   I upgraded TFS 2015 to TFS 2018 (6 months support window)

## 4.Decision and Validate

-   If you have any customization, you need to take decision. Do you
    want to keep it or not?
-   Note that there are customizations that are not supported. If you
    want to keep any of the supported customizations, you will need to
    use Hosted XML process model. Also note that you will not be able to
    move to the Inherited process model before 2019, as it is planned.
-   In my process of migration, I was using inherited process model.
    First, I removed all customization, then checked the log and fixed
    all errors, then revalidate again until no errors appeared.
-   In order to start the TFS Migrator validate, from the command line
    on the application tier, navigate to the tool directory and type the
    following:

```
TfsMigrator validate /collection:http://TFSServer:8080/tfs/CollectionName/
```

Now we should review validation warnings and errors. I got the
following messages displayed in the image below:

![Start TFS Migrator validate using command line](/assets/images/2018/03/Start-TFS-Migrator-validate-using-command-line.png "Start TFS Migrator validate using command line")

As we can see on the image, I have one error that I
have existing table with size of 45GBs, which is above recommended size
of 20GBs, meaning that I am not able to use
[DACPAC](https://docs.microsoft.com/en-us/sql/relational-databases/data-tier-applications/data-tier-applications)
import method. Here is the list of the some of the customizations, which
I have removed during my process of migration: 

-   List link types (listlinktypes)

```
witadmin listlinktypes /collection:http://TFSServer:8080/tfs/CollectionName/
```

-   Delete link type (deletelinktype)

``` 
witadmin deletelinktype /collection:http://TFSServer:8080/tfs/CollectionName/ /n:xxx.LinkTypes.Blocked
```

-   Change work item field (changefield)

```
witadmin changefield /collection:http://TFSServer:8080/tfs/CollectionName/ /n:xxx.Blocked /name:"Blocked (Custom)"
```


-   Destroy work item definitions (destroywitd)

``` 
witadmin destroywitd /collection:http://TFSServer:8080/tfs/CollectionName//p:"ProjectName" /n:"featureset"
```

## 5.Prepare

-   Once the validation is ok, we are ready to import
-   We need to run prepare command in order to generate import settings
    and related files:

```
TfsMigrator prepare /collection:http://TFSServer:8080/tfs/CollectionName/ /tenantDomainName:mydomain.onmicrosoft.com /accountRegion:WEU
```

Please note that in order to run this command you need [Azure Active Directory tenant](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-howto-tenant).
The prepare command will contact your Azure Active Directory tenant so
it will prompt you to login with a user from the tenant with permissions
to read information about all of the users in the Azure Active Directory
tenant.

-   It generates the default configuration file (settings.json, which is
    an input to the import service)
-   In my case I have two collections. One of them is that I used
    dacbac, and the second one is that I have table that exceed 45GBs so
    I had to use Azure VM with SQL Server

### 5.1.Prepare - First collection dacpac

-   Prepare Azure storage container for the dacpac
-   Detach collection
-   Create the dacpac file from the collection using the following
    command:

```
SqlPackage.exe /sourceconnectionstring:"Data Source=sqlserverName/instase;Initial Catalog=Tfs_CollectionDBName;Integrated Security=True" /targetFile:C:\MyCollection.dacpac /action:extract /p:ExtractAllTableData=true /p:IgnoreUserLoginMappings=true /p:IgnorePermissions=true /p:Storage=Memory
```

-   Upload (Azure Copy) the dacpac file to the Azure storage container

``` 
AzCopy /Source:"C:\myfolder" /Dest:https://mystorgeurl.blob.core.windows.net/tfsimport /DestSAS:"?st=xxxxx"
```

-   Change the import setting in the configuration file (setting.json)
    to point to the url of the storage container and you are ready to go

### 5.2.Prepare - Second collection Azure VM

-   Prepare the Azure VM with SQL Server
-   Detach collections
-   Backup the DB from the collection
-   Upload (using the Azure Copy) the DB backup file to the Azure
    storage container
-   Download DB backup to the SQL VM and restore it (using Download
    manager)
-   Change the configuration file (generated from the preparation first
    step) to point to the VM IP and also the SQL connection string and
    you are ready to go

## 6.Import

### 6.1.Import - Dry-run

Till now, I have Azure storage container with dacpac file and a database
backup restored on a SQL Server on a virtual machine. This is my source,
one tool settings file that have all the information needed for the
migration. The next step is to running the tool with the import as a
dry-run (trial migration). Run the TfsMigrator import command and define
the path to the configuration file which contains all the parameters for
the migration, as following:

```
TfsMigrator import /importFile:"C:\myfile.json"
```

![TfsMigrator import command](/assets/images/2018/03/TfsMigrator-import-command-1024x341.png "TfsMigrator import command")

Next, we are going to see the progress of the
import, as shown in the image bellow: 

![Progress of the import progress from TFS to VSTS](/assets/images/2018/03/Progress-of-the-import-progress-from-TFS-to-VSTS--1024x566.png "Progress of the import progress from TFS to VSTS")

Next on the screen we see a warning with
the following message: *This dry run account will expire and be deleted
shortly after 7:20 PM on 2/1/2018. To continue testing beyond this date
you will need to repeat the dry run import.

![TFS Migrator Dry run warning for expiring account](/assets/images/2018/03/TFS-Migrator-Dry-run-warning-for-expiring-account-1024x481-1024x310.png "TFS Migrator Dry run warning for expiring account")

### 6.2.Import - Production

-   Delete dry-run
-   Change the configuration into \"production\"
-   Re-run the import in the same way
-   Rename your account with the reserved name
-   Done

## Summary

Here is the quick overview of the all steps of the migration process.
Real migration process took about twelve continuous hours.

1.  Install and Upgrade to TFS 2018
2.  Remove all customization of all the projects
3.  Validate the process is ready
4.  Generate migration settings files for (preparation)
5.  Detach collections
6.  Dacpac The 1st collection
7.  Take backup 2nd collection
8.  Azure Copy the dacpac to the Azure storage container
9.  Azure Copy the DB backup to the Azure storage container
10. Download DB backup to SQL VM and restore it
11. Change the import setting and run the import for both collections

Your team is now on VSTS and will receive now updates frequently and
have many opportunities to implement tools and processes that will help
to be more effective in building quality software. If you would like
to see the video which go through all the steps, see the video below: 

{% include embed/youtube.html id='7C6LG6k4wcU' %}

