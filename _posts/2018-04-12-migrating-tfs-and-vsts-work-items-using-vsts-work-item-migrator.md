---
layout: post
title: "Migrating TFS and VSTS Work-items using vsts-work-item-migrator"
date:   2018-04-12 05:09:17 +0100
---

## Microsoft released new tool vsts-work-item-migrator.

It\'s a command line tool as an open source for migrating work-items
from **TFS and VSTS**. The tool developed in .NET Core, so it\'s cross
platform, it used Work-item REST API. So it\'s a great example for how
to consume that API, in this video. I am going to explain in step by
step, how to migrate work-items using this tools. That we will see how
to change the configuration to include the source and target projects
and use VSTS access token. We will see also some tricks about how to use
the tool. It will see how run the validation with dotnet WiMigrator.dll
-v configuration.json command and how to run the real migration with
dotnet WiMigrator.dll -m configuration.json command We just++ see how to
remove GUID tag to re-run the migration again and many others. -�

>If you would like to learn more about different tools
and ways for Team Foundation Server to Visual Studio Team Services
migration, - have a look at the [quick guide about real stories for
migrating Team Foundation Server to Visual Studio Team
Services](https://mohamedradwan-devops.github.io/posts/published-a-quick-guide-about-real-stories-for-migrating-team-foundation-server-to-visual-studio-team-services/).
The guide describes some of the real migration scenarios and explains
how to use different tools for several cases.
{: .prompt-tip }
{% include embed/youtube.html id='aHbiLYUfomc' %}

>You can see this video, if you would like to find more information about my personal experience
of the migration Team Foundation Server to Visual Studio Team Services
using Database Import Service or TFS Migrator tool provided by Visual
Studio Team. Going through all six phases of the migration, following
the migration guide provided by Microsoft as a walkthrough. You will see
how to get started with the migration process and which prerequisites
should be completed. The most important prerequisite is that you must
have Azure Active Directory in order to use TFS Migrator tool. See more
about the two different process models supported by VSTS, Inherited and
Hosted XML. See which decisions you should make and how to validate
them. For example which customizations you should keep and which one to
remove. To prepare the first collection dacpac, first you should prepare
Azure Storage Container, create dacpac file and afterwards upload it. To
prepare the second collection Azure VM, you should install SQL Server.
Backup the DB from the collection and upload it to the Azure storage
container. See first how to import (dry - run) and how to change the
configuration afterwards in order to import (production).
{: .prompt-tip }
{% include embed/youtube.html id='7C6LG6k4wcU' %}

