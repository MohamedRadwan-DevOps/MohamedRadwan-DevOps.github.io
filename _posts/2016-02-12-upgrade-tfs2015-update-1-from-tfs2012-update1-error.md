---
layout: post
title: "Upgrade TFS2015 Update 1 from TFS2012 Update1 error"
date:   2016-02-12 13:35:27 +0100
---

I was upgrading from TFS 2012 Update 1 to [TFS 2015 Update1](https://www.visualstudio.com/en-us/news/tfs2015-update1-vs.aspx), and encountered the following error:

```
TF400311: The database connection strings are not valid and cannot be
automatically corrected. To fix this problem, use the TFSConfig RemapDBs
command-line tool to correct the database connection
strings.
```

This happened because I didn\'t include the default collection database, as it was not
needed by the customer.

>The post [Upgrade to TFS 2018 Has Been Done in Production](https://mohamedradwan-devops.github.io/posts/upgrade-to-tfs-2018-has-been-done-in-production/)
describes a full upgrade and migration from TFS2015 to TFS2018 and
describes the improvements over the old TFS 2015.

[![TFS2015 Update1 Upgrade error](/assets/img/2016/02/tfs2015-update1-upgrade-error.jpg)](/assets/img/2016/02/tfs2015-update1-upgrade-error.jpg)


#### Upgrading from an older version of TFS to TFS 2015 Update 1

You can see [some estimated timelines and factors here](https://mohamedradwan-devops.github.io/posts/how-long-it-will-take-to-upgrade-to-tfs2015-with-update1/).

You can see **[this video](https://www.youtube.com/watch?v=7C6LG6k4wcU&t=4s)**,

If you would like to find more information about my personal experience
of the migration Team Foundation Server to Visual Studio.Team Services
using Database Import Service or TFS Migrator tool provided by Visual
Studio Team. Going through all six phases of the migration, following
the migration guide provided by Microsoft as a walk through. You will
see how to get started with the migration process and which
prerequisites should be completed.

The most important prerequisite is that you must have Azure Active
Directory in order to use TFS Migrator tool. See more about the two
different process models supported by VSTS, Inherited and Hosted XML.
See which decisions you should make and how to validate them. For
example which customizations you should keep and which one to remove. To
prepare the first collection dacpac, first you should prepare Azure
Storage Container, create dacpac file and afterwards upload it. To
prepare the second collection Azure VM, you should install SQL Server,
backup the DB from the collection and upload it to the Azure storage
container. See first how to import (dry - run) and how to change the
configuration afterwards in order to import (production).

