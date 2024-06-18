---
layout: post
title: "TFS 2017 Migration To VSTS with VSTS Sync Migrator"
date:   2017-09-15 08:00:30 +0100
---

## Introduction

In my previous [post](https://mohamedradwan-devops.github.io/posts/tfs-2017-migration-to-vsts-with-tfs-integration-platform/) I've described the migration between TFS and VSTS, using the [**TFS Integration Platform**](https://tfsintegration.codeplex.com). As described in that post, the tool is pretty simple and straightforward to use, but it doesn't support the migration of all artifacts, such as links between the work items. Besides that, I think it's worth mentioning again, that this migration tool is deprecated. If your migration demands high fidelity, then this tool would not be appropriate. For such cases, demanding high fidelity, [**VSTS Sync Migrator**](https://marketplace.visualstudio.com/items?itemName=nkdagility.vsts-sync-migration) is an appropriate solution. This tool is very powerful and was developed by [**Martin Hinshelwood**](https://nkdagility.com/company/about-martin-hinshelwood/), who is a fellow **ALM MVP**. The tool's strength comes from its coverage of all migration options. Migration with the VSTS Sync Migration Tool is a bit complicated, but it's a powerful option as we don't have limitations for migrating links, attachments, or work items.

>If you would like to learn more about my personal experience of migrating Team Foundation Server to Visual Studio Team Services using the Database Import Service or TFS Migrator, the TFS Database Import Service, also known shorthand as the Import Service, provides a high-fidelity way to migrate collection databases from TFS to VSTS. Have a look at [this post](https://mohamedradwan-devops.github.io/posts/migrating-team-foundation-server-to-visual-studio-team-services-using-database-import-service-tfs-migrator/).
{: .prompt-tip }

## Step 1: Getting Environment Ready

Before starting the migration, make sure to have:

1. [TFS Process Template Editor](https://marketplace.visualstudio.com/items?itemName=KarthikBalasubramanianMSFT.TFSProcessTemplateEditor) extension for [Visual Studio](https://www.visualstudio.com) installed.
2. Open The Process Editor Extension in Visual Studio.
3. Download & Install [VSTS Sync Migrator](http://vsts-bulk-editor.readthedocs.io/en/latest/getting-started/).
4. Open Command Prompt or [PowerShell](https://msdn.microsoft.com/en-us/powershell/mt173057.aspx).
5. Navigate with CMD or PS to a new folder (Recommended).
6. Run the command `vstssyncmigrator init` to create a default configuration.
7. Open "vstsbulkeditor.json" file from the same directory.

## Step 2: Preparing TFS

For the migration to succeed, we need to have an additional field in both TFS & VSTS for tracking purposes (this is essential for the tool to be able to link work items to each other).

1. Open Visual Studio.
2. Open the Tools Menu.
3. Open the Process Editor Menu.
4. Open Work Item Types.
5. Click Open WIT From Server.

![VSTS_Sync_Mig_Update_TFS_Fields](/assets/images/2017/09/VSTS_Sync_Mig_Update_TFS_Fields-1-1024x566.png)

**For each of the Work Item Types in your Project**, do the following:

6. Click On New.
7. Set the Field Name to **ReflectedWorkItemId**.
8. Make sure it's of type **String**.
9. Set the Reference Name to **TfsMigrationTool.ReflectedWorkItemId**.
10. Click OK.
11. The field is now added.

![VSTS_Sync_Mig_Update_TFS_Fields_2](/assets/images/2017/09/VSTS_Sync_Mig_Update_TFS_Fields_2-1-1024x564.png)

**Important Note:** Make sure to add the field to all Work Item Types.

[More Info]{.ion-info} The post [Upgrade to TFS 2018 Has Been Done in Production](https://mohamedradwan-devops.github.io/posts/upgrade-to-tfs-2018-has-been-done-in-production/) describes a full upgrade and migration from TFS2015 to TFS2018 and describes the improvements over the old TFS 2015.

## Step 3: Preparing VSTS

We need to also modify Work Items in VSTS to match with TFS, so the tool can complete the Migration Process.

1. Open your **VSTS Account Settings**.
2. Open **Process Settings**.

![VSTS_Settings_Process](/assets/images/2017/09/VSTS_Settings_Process-1-1024x507.png)

3. Open Your **Inherited Process Settings**.

![Open_Inh_Process](/assets/images/2017/09/Open_Inh_Process-1-1024x422.png)

4. For Each Work Item Type, open it and repeat the following steps:

![VSTS_Edit_WIT](/assets/images/2017/09/VSTS_Edit_WIT-1-1024x472.png)

5. Click Add New.
6. In the New Field Dialog, set the New Field name to **ReflectedWorkItemId**.
7. Make sure it's of Type **Text Single Line**.
8. Click **Add Field**.

![VSTS_Add_Field_To_WIT](/assets/images/2017/09/VSTS_Add_Field_To_WIT-1-1024x519.png)

**Make sure you have added the field to all Work Item Types**. You can check Work Items (to make sure you have added the field) by going to your Inherited Process and checking the Work Item.

![Check_New_Field](/assets/images/2017/09/Check_New_Field-1-1024x521.png)

[Tip]{.ion-tip} If you would like to learn more about different tools and ways for Team Foundation Server to Visual Studio Team Services migration, have a look at the [quick guide about real stories for migrating Team Foundation Server to Visual Studio Team Services](https://mohamedradwan-devops.github.io/posts/published-a-quick-guide-about-real-stories-for-migrating-team-foundation-server-to-visual-studio-team-services/). The guide describes some real migration scenarios and explains how to use different tools for several cases.

## Step 4: Preparing JSON File

Do you remember the file we opened in Step 1.7? Let's get back to this file to adjust a few things before starting the migration.

1. In the source, we add information for the old TFS. We will add the **URL for the old TFS under the Collection option** and the **old project name under the Name Option**.
2. In the target, we add information for VSTS. We will add the **URL for the VSTS under the Collection option** and the **VSTS project name under the Name option**.
3. In the ReflectedWorkItemIdFieldName option, add the Name of your inherited Process followed by a period and "ReflectedWorkItemId". It should look like this: `MyInheritedProcessName.ReflectedWorkItemId`.
4. Put the **same value from step 3 in the targetField Option**.

![JSON_1](/assets/images/2017/09/JSON_1-1-1024x545.png)

5. Optional: You can use the valueMapping to change states of work items being migrated. This can be helpful if you're migrating between Scrum and Agile (or vice versa).

![JSON_2](/assets/images/2017/09/JSON_2-1-1024x545.png)

6. Optional: WorkItemTypeDefinition is used to map Work Item Names. This should also be used if you're migrating between Scrum and Agile.
7. Processors are the control units for migration. Each processor controls the migration of a specific part of TFS. **If you don't have any processor enabled, the tool won't work at all.**
8. Each processor has an ObjectType, which is the name for the Object being migrated.
9. Each processor has an Enabled flag, which is either true or false. If it's enabled (true) then this processor will be executed during migration.

![JSON_3](/assets/images/2017/09/JSON_3-1-1024x546.png)

## Step 5: Migrate Work Iterations

The first thing we should migrate is the work iterations. This is known in the file with Object Type VSTSSyncMigrator.Engine.Configuration.Processing.NodeStructureMigrationConfig. As we can see on VSTS, we have no iterations (except the parent node):

![Empty_Iteration](/assets/images/2017/09/Empty_Iteration-1-1024x519.png)

2. To migrate iterations and their structure, let's get back to the JSON file. **Set the Enabled flag for the Object VSTSSyncMigrator.Engine.Configuration.Processing.NodeStructureMigrationConfig to true, otherwise the tool won't run this part.**

![1_Node_Structure_Migration](/assets/images/2017/09/1_Node_Structure_Migration-1-1024x545.png)

3. Run the following command: `vstssyncmigrator.exe execute --config vstsbulkeditor.json`.

![2_CMD_Node_Start](/assets/images/2017/09/2_CMD_Node_Start.jpg)

4. This might take a minute or less. Once finished, you'll see something like this:

![3_CMD_Node_Done](/assets/images/2017/09/3_CMD_Node_Done-1-1024x478.png)

>If you would like to know more about Azure deployments, have a look at the post [How to deploy to Azure using Team Services Release Management](https://mohamedradwan-devops.github.io/posts/how-to-deploy-to-azure-using-team-services-release-management/). The post describes how Azure deployments are made easy by using Visual Studio Team Services (VSTS) Release Management. You will see a step-by-step tutorial on how to configure and deploy to Azure in Release Management, and, moreover, how to configure an end-to-end pipeline for deploying applications on Azure.
{: .prompt-info}

## Step 6: Migrating Work Items

Now let's move to migrating the work items themselves. Here is the VSTS before migrating any work items. Here is a query on the new VSTS (lists all items in tree view) which shows that we have nothing yet.

![Empty_Backlog](/assets/images/2017/09/Empty_Backlog-1-1024x511.png)

Now let's start migrating work items:

1. Open the file again and make sure to set the **Object VSTSSyncMigrator.Engine.Configuration.Processing.NodeStructureMigrationConfig to false. This is very important**.
2. We have two options for migrating work items, as described below.
3. The first option is to migrate work items with their recent state, which means that the history of work items will be lost (VSTSSyncMigrator.Engine.Configuration.Processing.WorkItemMigrationConfig).
4. The second option is to migrate work items with their history (VSTSSyncMigrator.Engine.Configuration.Processing.WorkItemRevisionReplayMigrationConfig).
5. I'll choose migration with history, so we'll set the Enabled flag for it to be true.

![JSON_Migrate_Work_Items](/assets/images/2017/09/JSON_Migrate_Work_Items-1024x549.jpg)

6. Open the command prompt again and run the same command: `vstssyncmigrator.exe execute --config vstsbulkeditor.json`.

![Run_WIT_Migration](/assets/images/2017/09/Run_WIT_Migration-1-1024x478.png)

7. The last step might take some time depending on how many work items there are. In my case, it took around 17 minutes.

![CMD_Mig_WIT_Done](/assets/images/2017/09/CMD_Mig_WIT_Done-1-1024x479.png)

Here is how VSTS looks after migration. Remember that **so far we have only migrated Work Items, but with no links between them and no attachments**.

![Full_Backlog](/assets/images/2017/09/Full_Backlog-2-1024x518.png)

## Step 7: Migrating Links between Work Items

Now it's time to migrate the links between work items. I added one more column to demonstrate that, as we can see the links between work items count is zero.

![No_Count_For_Links](/assets/images/2017/09/No_Count_For_Links-1-1024x503.png)

So let's get back to the file:

1. Open the file again and make sure to set the **Object VSTSSyncMigrator.Engine.Configuration.Processing.WorkItemRevisionReplayMigrationConfig to false. This is very important**.
2. Find the **Object VSTSSyncMigrator.Engine.Configuration.Processing.LinkMigrationConfig**.
3. Set the Enabled flag for this object to true.

![JSON_Migrate_Links](/assets/images/2017/09/JSON_Migrate_Links-1024x529.jpg)

4. Open the command prompt again and run the same command: `vstssyncmigrator.exe execute --config vstsbulkeditor.json`.
5. This could take a few minutes.

![CMD_Mig_Links_Done](/assets/images/2017/09/CMD_Mig_Links_Done-1-1024x479.png)

6. If we check VSTS again, we'll see that links have been migrated.

![VSTS_After_Migration_Links](/assets/images/2017/09/VSTS_After_Migration_Links-1-1024x476.png)

>If you would like to learn more about enhancing frontend development code quality, it includes understanding different types of JavaScript unit testing frameworks like Jasmine, Mocha, Jest, different types of task runners like Grunt and Gulp, different types of linting tools like JSHint, ESLint, JSLint, CSSLint, and different types of code formatters like Prettier and Tidy.
{: .prompt-tip }

Learn how to write your first JavaScript unit test with the Jasmine standalone version, how to run JavaScript unit tests using Grunt, Command Line, and PhantomJS, how to calculate code coverage for JavaScript unit tests using Istanbul, how to run JavaScript unit tests using Visual Studio Test Explorer using the Chutzpah extension, how to lint JavaScript code using JSHint and how to run that from the Command Line using Grunt. Finally, it shows how to integrate all the quality practices with Visual Studio Team Service Build automation so it can be part of CI/CD or Continuous Integration and Continuous Delivery. Have a look at [this post](https://mohamedradwan-devops.github.io/posts/front-end-code-quality-javascript-unit-test-and-linting-automation-with-vsts-build/).

## Step 8: Migrating Attachments

Now attachments for Work Items is the only remaining thing, as we can see the attachments count is zero.

![No_Attachment](/assets/images/2017/09/No_Attachment-1-1024x476.png)

Let's get back to the file:

1. Open the file again and make sure to set the **Object VSTSSyncMigrator.Engine.Configuration.Processing.LinkMigrationConfig to false. This is very important**.
2. For migrating attachments, we need two options to be enabled (true), not only one. The options are:

    1. **VSTSSyncMigrator.Engine.Configuration.Processing.AttachmentExportMigrationConfig**
    2. **VSTSSyncMigrator.Engine.Configuration.Processing.AttachmentImportMigrationConfig**

    **Both of them should be set to true**.

![JSON_Attachments](/assets/images/2017/09/JSON_Attachments-1-1024x541.png)

3. Open the command prompt again and run the same command: `vstssyncmigrator.exe execute --config vstsbulkeditor.json`.

![CMD_Mig_Att](/assets/images/2017/09/CMD_Mig_Att-1-1024x478.png)

4. This might take a few minutes.

![CMD_Mig_Att_Done](/assets/images/2017/09/CMD_Mig_Att_Done-2-1024x478.png)

5. Now let's check the Attachment Count in VSTS again.
6. Finally, here are the Work Items in VSTS with attachments migrated.

![VSTS_Att_Mig_Done](/assets/images/2017/09/VSTS_Att_Mig_Done-1024x485.jpg)

>If you would like to learn more about how to change the credential of an IIS Application Pool using PowerShell, and how to restart the Application Pool using PowerShell, have a look at [this post](https://mohamedradwan-devops.github.io/posts/working-with-iis-powershell/).
{: .prompt-info}

## Conclusion

**VSTS Sync Migrator** is a very powerful tool developed by [**Martin Hinshelwood**](https://nkdagility.com/company/about-martin-hinshelwood/). The tool allows migrating high-fidelity work items between TFS and VSTS, including Work Items, Iterations, Attachments, Links between work items, and even more options found in the [official documentation](http://vsts-bulk-editor.readthedocs.io/). The tool still requires a bit of experience and understanding of both TFS and VSTS, but it's really valuable as it covers migrating many project artifacts.

