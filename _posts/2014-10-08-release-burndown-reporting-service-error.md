---
layout: post
title: "Release Burndown Reporting Service Error"
date:   2014-10-08 15:41:13 +0100
---

In [Team Foundation Server](http://msdn.microsoft.com/en-us/vstudio/ff637362.aspx "Visual Studio Team Foundation Server 2013"), if you use the Scrum template and all reports deployed to SharePoint are working properly except for the "Release Burndown" report not working, you may encounter the following error:

>Parameter validation failed. It is not possible to provide valid values for all parameters. (rsParameterError) sql reporting
{: .prompt-danger }

![TFS Reporting Service error](/assets/img/2014/10/tfs-reporting-service-error.png)

You only need to give start and end dates for iterations:

![Add start date and end date for iteration tfs](/assets/img/2014/10/add-start-date-and-end-date-for-iteration-tfs.png)

Remember, you will need to wait for the warehouse job to run or just manually run it, [click here for more info](https://mohamedradwan-devops.github.io/posts/process-the-tfs-data-warehouse-manually/ "Process the TFS Data Warehouse and Analysis Service manually").

You should not see the error again even if you don't have data.

![Release burndown TFS reporting service fix](/assets/img/2014/10/release-burndown-tfs-reporting-service-fix.png)
