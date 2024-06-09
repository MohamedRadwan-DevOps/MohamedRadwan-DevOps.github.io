---
layout: post
title: "Migration to VSO (Visual Studio Online) with different tools"
date:   2015-05-14 22:34:26 +0100
---

I had an assignment which required migrating all TFS on-premises to VSO (Visual Studio Online), this includes TSF2010, TFS2012 and TFS2013 I will try to explain most of the process and the steps.

1. [Problem](#problem)
2. [Migrating work-items using OpsHub](#migrating-work-items-using-opshub)
   1. [Solution Summary](#solution-summary)
   2. [Solution Details](#solution-details)
   3. [Solution Notes](#solution-notes)
3. [Migrating work-items using TFS Integration Platform](#migrating-work-items-using-tfs-integration-platform)
   1. [Solution Summary](#solution-summary-1)
   2. [Solution Details](#solution-details-1)
   3. [Solution Notes](#solution-notes-1)
4. [Migrating Source control using OpsHub](#migrating-source-control-using-opshub)
   1. [Solution Summary](#solution-summary-2)
   2. [Solution Details](#solution-details-2)
   3. [Solution Notes](#solution-notes-2)
5. [Migrating Source control using TFS Integration Platform](#migrating-source-control-using-tfs-integration-platform)
   1. [Solution Summary](#solution-summary-3)
   2. [Solution Details](#solution-details-3)
6. [Overall Notes](#overall-notes)
7. [Links](#links)

## Problem

VSO (Visual Studio Online) doesn’t support customization yet. The first server for my assignment was TFS-2010 and most projects were customized based on a combination between MSF for CMMI process template v.4.0, v.5.0 and also some work-items from different Agile templates.

## Migrating work-items using OpsHub

### Solution Summary

The free version of OpsHub required the process template of the project matching an existing one of the standard process templates (Agile, CMMI or Scrum), so in order to migrate a project we need to transform it into Agile v.5.0 (TFS2010) and migrate work-items as the following:

- Importing work-items that don’t exist (Issue) from Agile v.5.0
- Copy existing work-items that do not belong to Agile into other work-items types of Agile v.5.0
  - (Change request → Issue)
  - (Requirement → User Story)
- Change Categories by removing the usage of non-Agile work-items
- Destroy non-Agile work-items types (Change request - Requirement)
- Change some of the system fields' names to match the new work-items types of the Agile v.5.0
- Import all Agile v.5.0 work-items (User Story, Bug, Test Case, Issue, Shared Steps)
- Verify that the current project matches 100% of the Agile v.5.0
- Running work-items migration using OpsHub tool

### Solution Details

- **Importing work-items that don’t exist (Issue) from Agile v.5.0**

  Downloaded Agile v.5.0 process template from TFS
  ![image001](/assets/images/2015/05/image001.jpg?w=660)

  ![image002](/assets/images/2015/05/image002.jpg)

  Open TFS Team Project Manager, select the project and navigate to Work item configuration/work items types/import. Click add and select Issue work-item from Agile v5.0 work-items and click on import.
  ![image003](/assets/images/2015/05/image003.jpg?w=660)

  I could also import it using WitAdmin command line
  ![image004](/assets/images/2015/05/image004.jpg)

- **Copy existing work-items that do not belong to Agile into another work-item types of Agile v.5.0**
  - **(Change request → Issue)**
  - **(Requirement → User Story)**

  1. Make a query that includes all the work-items we want to copy into other types
  2. Open the query result in Excel
  3. Copy all rows except the Work Item Type
  4. Change the Work Item Type into the desired type
  5. Click publish to publish new work-items

  ![image005](/assets/images/2015/05/image005.jpg?w=660)

- **Change Categories by removing the usage of non-Agile work-items**

  1. The Requirement category was referencing the Requirement work-item as the default work-item, and since we will remove that work-item as it’s not part of Agile v5.0 and also to make the categories match Agile v5.0 process template, we had to change the category to reference User Story instead of Requirement.
  2. Open TFS Team Project Manager, select the project and navigate to Work item configuration/Categories/Update & import/Load From Team Project and select the current project.
  3. Change the default work-item for the Requirement category from Requirement to User Story.
  4. Click Import work-items category.

  ![image006](/assets/images/2015/05/image006.jpg?w=660)

- **Destroy non-Agile work-items types (Change request - Requirement)**

  This also will delete all work-items from TFS DB for those types. Run the following 2 commands from WitAdmin command line tool:

  ```sh
  witadmin.exe destroywitd /collection:http://kbndvtfs01:8080/tfs/TempVSO2 /p:ServicesVSO /n:"Requirement"
  witadmin.exe destroywitd /collection:http://kbndvtfs01:8080/tfs/TempVSO2 /p:ServicesVSO /n:"Change Request"
```

![image007](/assets/images/2015/05/image007.jpg?w=660)

- **Change some of the system fields name to match the new work-items types of the Agile v.5.0**

Test Case:
```sh
witadmin changefield /collection:http://kbndvtfs01:8080/tfs/TempVSO2 /n:"System.ExternalLinkCount" /name:"External Link Count"
witadmin changefield /collection:http://kbndvtfs01:8080/tfs/TempVSO2 /n:"System.RelatedLinkCount" /name:"Related Link Count"
witadmin changefield /collection:http://kbndvtfs01:8080/tfs/TempVSO2 /n:"System.HyperLinkCount" /name:"Hyperlink Count"
witadmin changefield /collection:http://kbndvtfs01:8080/tfs/TempVSO2 /n:"System.AttachedFileCount" /name:"Attached File Count"
witadmin changefield /collection:http://kbndvtfs01:8080/tfs/TempVSO2 /n:"System.AreaId" /name:"Area ID"
witadmin changefield /collection:http://kbndvtfs01:8080/tfs/TempVSO2 /n:"System.IterationId" /name:"Iteration ID"
```

![image008](/assets/images/2015/05/image008.jpg?w=660)

-   **Import all Agile v.5.0 work-items (User Story, Bug, Test Case,
    Issue, Shared Steps)**

1.  Open TFS Team Project Manager, select the project and navigate to
    Work item configuration/work items types/import
2.  Click add and select all Agile v5.0 work-items and click on import

![image009](/assets/images/2015/05/image009.jpg?w=660)

-   **Verify that current project matching 100% of the Agile v.5.0**

1.  Open TFS Team Project Manager, select the project and navigate to
    Work item configuration/compare
2.  Click add and select all Agile v5.0 work-items and click on Compare
    Team Project With Source
3.  Make sure it 100%

-   **Running work-items migration using OpsHub tool**

Make sure that the account that you logged-in and will be used for the
migration added in Project Collection Service Accounts
group.

![image011](/assets/images/2015/05/image011.png?w=660)

Make sure that you++have a project with the same name and with the
process template that match the desired process
template

![image012](/assets/images/2015/05/image012.jpg?w=660)

Run OpsHub and select New Migration

![image013](/assets/images/2015/05/image013.jpg?w=660)

Select the source collection (local) and the destination account (VSO)

![image014](/assets/images/2015/05/image014.jpg?w=660)

Choose I want to migrate work-item and click on Next

![image015](/assets/images/2015/05/image015.jpg?w=660)

Select the destination project on VSO (Visual Studio Online) and click
Next

![image016](/assets/images/2015/05/image016.jpg?w=660)

Map the local users to the online users and click Next

![image017](/assets/images/2015/05/image017.jpg?w=660)

![image018](/assets/images/2015/05/image018.jpg?w=660)

Make sure that the verification running successfully

![image019](/assets/images/2015/05/image019.jpg?w=660)

Start the migration

![image020](/assets/images/2015/05/image020.jpg?w=660)

Review that the migration ran successfully

![image021](/assets/images/2015/05/image021.jpg?w=660)

### [3.Solution Notes:]

-   OpsHub free version doesn\'t support migration from TFS on- premises
    to TFS on-premises
-   OpsHub free version required that you migrate to the same project
    name
-   Migrating (copying work-items) using MS Excel will lose the history
    and the attachments

## [3.Migrating work-items using TFS Integration Platform]

### [1.Solution Summary]

Using TFS Integration Platform we can make custom mapping to map
work-items to different types and also mapping work-item\'s fields to
different fields, so we will not changing the process template of the
project also I will not map all fields so I can show how to resolve
conflicts for undefined fields

-   Run TFS Integration Platform
-   Use a custom mapping file (Doesn\'t map all required fields)
-   Show how to resolve conflict for none found fields
-   Continue migration

### [2.Solution Details]

-   Run TFS Integration Platform

After launching the tool, click on Create New

![image022](/assets/images/2015/05/image022.jpg?w=660)

Select workItemTracking.xml

![image023](/assets/images/2015/05/image023.jpg)

In the left side select the source (on-prem), in the right side select
VSO (Visual Studio Online), make sure that workflow type is
One-way-migration, click on Edit XML

![image024](/assets/images/2015/05/image024.jpg?w=660)

Put the mapping file

![image025](/assets/images/2015/05/image025.jpg?w=660)

Review how the mapping file translated by TFS Integration Tool, click on each work-item
mapping to see the details of the mapping fields, click save to
DB

![image026](/assets/images/2015/05/image026.jpg?w=660)

Click on Start

![image027](/assets/images/2015/05/image027.jpg)

The first conflict raised because a field in a work-item from the source
not exist in the destination work-item, we can choose the first option
which include typing the field that we want to map source field and
click resolve.

![image028](/assets/images/2015/05/image028.jpg?w=660)

I chose second option to ignore that filed

![image029](/assets/images/2015/05/image029.jpg?w=660)

Make sure that the conflict resolved (green icon) and click start

![image030](/assets/images/2015/05/image030.jpg?w=660)

The second conflict raised because the second field that not exist, I
will solve this conflict with another way, click on View Rules

![image031](/assets/images/2015/05/image031.jpg?w=660)

Double click on the rule to view the rule details, review the
information, take care of the scope that identify where to apply the
rule

![image032](/assets/images/2015/05/image032.jpg?w=660)

To solve the conflict, right click on the rule and select copy rule.

![image033](/assets/images/2015/05/image033.jpg?w=660)

In the InvalidFieldRefreneceName I will put the name of the missing
field, I also put it as the description but this is not important, I
will leave the scope with no change as I only need that scope.

![image034](/assets/images/2015/05/image034.jpg?w=660)

Click preview, this will display all work-items under that scope, select
the work-item and click resolve

![image035](/assets/images/2015/05/image035.jpg?w=660)

Review that second rule created successfully after resolve the conflict,
click start to continue the migration process

![image036](/assets/images/2015/05/image036.jpg?w=660)

### [3.Solution Notes:]

-   When you resolve a conflict, this built a rule, you may want to
    create a rule to solve conflict in case you want to change the
    default scope for the automatically created rule.
-   You don\'t need to restart the migration as the tool can continue
    for the conflicted items
-   Be careful of how to exclude fields in the mapping file
-   TFS Integration platform not support new features anymore

## [3.Migrating Source control using OpsHub]

### [1.Solution Summary]

Just run the free version of OpsHub to migrate the source code

### [2.Solution Details]

Make sure that the account that you logged-in and will be used for the
migration added in Project Collection Service Accounts group.

![image011](/assets/images/2015/05/image011.png?w=660)

Make sure that you have a project with the same name, it\'s not
important to match the process template unless you plan to migrate
work-items using the free version of OpsHub too

![image012](/assets/images/2015/05/image012.jpg?w=660)

Run OpsHub and select New Migration

![image013](/assets/images/2015/05/image013.jpg?w=660)

Select the source collection (local) and the destination account (VSO)

![image014](/assets/images/2015/05/image014.jpg?w=660)

Choose I want to migrate version control data and click on Next

![image037](/assets/images/2015/05/image037.jpg?w=660)

Select the destination project on VSO (Visual Studio Online) and click
Next

![image016](/assets/images/2015/05/image016.jpg?w=660)

Map the local users to the online users and click Next

![image017](/assets/images/2015/05/image017.jpg?w=660)

![image018](/assets/images/2015/05/image018.jpg?w=660)

Make sure that the verification running successfully Start the migration
Review that the migration ran successfully

![image038](/assets/images/2015/05/image038.png?w=660)

### [3.Solution Notes:]

-   You must add all users with their license before migration take
    place so we can map them to the local users as the tool only shows
    the licensed users
-   The tool heavily consumed CPU hence it needs a good machine with
    good CPU and RAM, it took about 3 hours to migrate source code that
    took only 10 minutes to be migrated using TFS Integration Platform

## [4.Migrating Source control using TFS Integration Platform]

### [1.Solution Summary]

Just run the TFS Integration platform and migrate the code

### [2.Solution Details]

Make sure that the account that you logged-in and will be used for the
migration added in Project Collection Service Accounts group.

![image011](/assets/images/2015/05/image011.png?w=660)

-   **Run TFS Integration Platform**

After launching the tool, click on Create New

![image022](/assets/images/2015/05/image022.jpg?w=660)

Select VersionControl.xml

![image039](/assets/images/2015/05/image039.jpg)

In the left side select the source (on-prem), in the right side select
VSO (Visual Studio Online), make sure that workflow type is
One-way-migration

![image040](/assets/images/2015/05/image040.jpg?w=660)
Because when we create a new project on VSO it create the folder
\"BuildProcessTemplate\", this makes a conflict during the migration as
it exists on both sides(Source and Destination) the manual resolve
couldn\'t solve this conflict.

![image041](/assets/images/2015/05/image041.jpg?w=660)

We could destroy those folders on any++side to solve the conflict but I
thought it\'s better to just map all other folders except that one

![image042](/assets/images/2015/05/image042.jpg?w=660)

Start the migration

![image043](/assets/images/2015/05/image043.jpg?w=660)

If your source code use branches you may encounter the following
conflict \"VC path not mapped conflict type\" and because we want the
history as much as possible, we will chose \"Add\' for \'Branch\', by
skipping for \'Merge\' and by changing to \'Add\' for Remove\" and click
resolve. Remember that we could change the resolving scope by create a
rule instead of resolving by applying the automatic rule

![image044](/assets/images/2015/05/image044.jpg?w=660)

Continue the migration by clicking on Start

![image045](/assets/images/2015/05/image045.jpg?w=660)


## [6.Overall Notes:]

WARNING: Always do the migration on a test environment first before you
ever touch production and before touch the production always backup
first. It\'s recommended that developers test the migration on a testing
environment before making the live migration VSO (Visual Studio Online)
doesn\'t support multiple collection yet but we can create multiple
accounts that has different default collection

## [7.Links:]

[Migrating On Premises TFS to VS Online (Brian Harry)](http://blogs.msdn.com/b/bharry/archive/2014/05/14/migrating-on-premises-tfs-to-vs-online.aspx)
[Migrating Your Data from TFS to Visual Studio Online with New Free Utility from OpsHub (Ed Blankenship)](http://blogs.msdn.com/b/visualstudioalm/archive/posts/migrating-your-data-from-tfs-to-visual-studio-online-with-new-free-utility-from-opshub.aspx)

[Migrate team projects from on-premises TFS to Visual Studio Online MSDN)](https://www.visualstudio.com/get-started/setup/migrate-team-projects-vs)

[TOC: TFS Integration Tools Blog Posts and Reference Sites](http://blogs.msdn.com/b/willy-peter_schaub/archive/2011/06/06/toc-tfs-integration-tools-blog-posts-and-reference-sites.aspx)
[TFS Integration Platform - Summary of Links](http://blogs.msdn.com/b/willy-peter_schaub/archive/2009/10/07/tfs-integration-platform-summary-of-links.aspx)
[How to Assign licenses to users on VSO](https://www.visualstudio.com/get-started/setup/assign-licenses-to-users-vs#ConnectedDirectory)
[How to integrate VSO with Azure AD](https://www.visualstudio.com/get-started/setup/manage-organization-access-for-your-account-vs)

