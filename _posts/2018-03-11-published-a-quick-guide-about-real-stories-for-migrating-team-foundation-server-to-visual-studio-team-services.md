---
layout: post
title: "Published a quick guide about real stories for migrating Team Foundation Server to Visual Studio Team Services"
date: 2018-03-11 18:18:45 +0100
---

### I published a quick guide about real stories for migrating [Team Foundation Server](https://www.visualstudio.com/tfs/) to [Visual Studio Team Services](https://www.visualstudio.com/team-services/).

It describes some real migration scenarios and explains how to use different tools by the example of several migration cases. Many of the migration principles described in the guide can be used not only for **TFS** to **VSTS** migration but also for migration from an older **TFS** version to a newer one as well. Find out more details in the guide. [Download the guide](https://gallery.technet.microsoft.com/Real-stories-for-migrating-11357e61){target="_blank" rel="noopener noreferrer"}.

>You can see this video, if you would like to find more information about my personal experience of migrating Team Foundation Server to Visual Studio Team Services using the Database Import Service or TFS Migrator tool provided by the Visual Studio Team. Going through all six phases of the migration and following the migration guide provided by Microsoft as a walkthrough. You will see how to get started with the migration process and which prerequisites should be completed. The most important prerequisite is that you must have Azure Active Directory in order to use the TFS Migrator tool.
See more about the two different process models supported by VSTS: Inherited and Hosted XML. See which decisions you should make and how to validate them, for example which customizations you should keep and which to remove. To prepare the first collection dacpac, first you should prepare the Azure Storage Container, create the dacpac file, and afterwards upload it. To prepare the second collection Azure VM, you should install SQL Server, back up the DB from the collection, and upload it to the Azure storage container. See first how to import (dry run) and how to change the configuration afterwards in order to import (production).
{: .prompt-tip }
{% include embed/youtube.html id='7C6LG6k4wcU' %}

![3-D Cover](/assets/images/2018/03/3-D-Cover.png)[Download the guide](https://gallery.technet.microsoft.com/Real-stories-for-migrating-11357e61)

>If the migration demands high fidelity for work items, the post [TFS 2017 Migration To VSTS with VSTS Sync Migrator](https://mohamedradwan-devops.github.io/posts/tfs-2017-migration-to-vsts-with-vsts-sync-migrator/) describes the migration without any limitations for migrating links and attachments.
{: .prompt-info }

>If the migration process only requires migrating the work items, with no need to migrate links and relations between them, you can consider using the [TFS Integration Platform](https://marketplace.visualstudio.com/items?itemName=Willy-PSchaub.TeamFoundationServerIntegrationToolsMarch2012Relea), which is less complicated than the VSTS Sync Migrator. For more information about this tool, visit [TFS 2017 Migration To VSTS with TFS Integration Platform](https://mohamedradwan-devops.github.io/posts/tfs-2017-migration-to-vsts-with-tfs-integration-platform/).
{: .prompt-info }

