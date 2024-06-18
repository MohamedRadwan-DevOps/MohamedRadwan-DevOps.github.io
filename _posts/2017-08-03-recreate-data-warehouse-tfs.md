---
layout: post
title:  "How to recreate the Data warehouse and the Analysis service for TFS?"
date:   2017-08-03 07:40:05 +0100
---

2 days ago I have a problem seeing my reports on the TFS and after the investigation I solve part of the problem which is how to recreate the data warehouse and the analysis service for the TFS, my problem was that
when you open any reports you find the following error

> Query execution failed for dataset \'dsIteration\'.
> (rsErrorExecutingCommand) Get Online Help Errors in the metadata
> manager. An error occurred when loading the Team System cube, from the
> file, \'\\?C:Program FilesMicrosoft SQL
> ServerMSAS10.MSSQLSERVEROLAPDataTfs_Analysis.0.dbTeam
> System.636.cub.xml\'. Errors in the metadata manager. An error
> occurred when loading the Work Item dimension, from the file,
> \'\\?C:Program FilesMicrosoft SQL
> ServerMSAS10.MSSQLSERVEROLAPDataTfs_Analysis.0.dbvDimWorkItemOverlay.187.dim.xml\'.
> File system error: The following file is corrupted: Physical file:
> \\?C:Program FilesMicrosoft SQL
> ServerMSAS10.MSSQLSERVEROLAPDataTfs_Analysis.0.dbvDimWorkItemOverlay.147.dim187.Hierarchy.Area1.sstore.
> Logical file

And when I go to the analysis service and try to see it, it gives me the
following error.

> File system error: The following file is corrupted: Physical file:
> \\?C:Program FilesMicrosoft SQL
> ServerMSAS10.MSSQLSERVEROLAPDataTfs_Analysis.0.dbvDimWorkItemOverlay.147.dim187.Hierarchy.Area1.sstore.
> Logical file . Errors in the metadata manager. An error occurred when
> loading the Work Item dimension, from the file, \'\\?C:Program
> FilesMicrosoft SQL
> ServerMSAS10.MSSQLSERVEROLAPDataTfs_Analysis.0.dbvDimWorkItemOverlay.187.dim.xml\'.
> Errors in the metadata manager. An error occurred when loading the
> Team System cube, from the file, \'\\?C:Program FilesMicrosoft SQL
> ServerMSAS10.MSSQLSERVEROLAPDataTfs_Analysis.0.dbTeam
> System.636.cub.xml\'. (Microsoft.AnalysisServices)

I can\'t even right-click and see the property of the Analysis data So here the solution to this problem

- Stop the analysis service and delete the Tfs_Analysis.0.db folder

[![Stop the analysis service](/assets/images/2017/08/Stop-analysis-service.png)](/assets/images/2017/08/Stop-analysis-service.png)

[![Delete Tfs_Analsysis.0.db](/assets/images/2017/08/Analysis-service-data-folder.png)](/assets/images/2017/08/Analysis-service-data-folder.png)

- Go the report on the Team foundation administration console and edit the property, you can create new names if you want for the data warehouse or the analysis service if you want but you must use the appropriate service account that you used when you first configure and install the system

[![Edit the report tab](/assets/images/2017/08/Edit-report-configuration.png)](/assets/images/2017/08/Edit-report-configuration.png)

- Start rebuild the data warehouse and the analysis service, this command will rebuild them again from the TFS DB

[![Rebuild the data warehouse and analysis service](/assets/images/2017/08/Rebuild-the-data-warehouse-and-the-reports.png)](/assets/images/2017/08/Rebuild-the-data-warehouse-and-the-reports.png)


- Go to the Team Project collection and choose your collection and click report folder

[![Create Report folder](/assets/images/2017/08/Assign-report-folder.png)](/assets/images/2017/08/Assign-report-folder.png)

- Enter the name of the folder that will hold your reports

[![Give the report folder name](/assets/images/2017/08/Naming-Report-folder.png)](/assets/images/2017/08/Naming-Report-folder.png)

If you want to see the reports immediately, you will need to process the Data-warehouse and the Analysis service from the web services, or just leave it when the schedule job is running, for the step-by-step on how to process this manually just see the following post. 

[Process theTFS Data Warehouse and Analysis Service manually](https://mohamedradwan-devops.github.io/2011/07/11/process-the-tfs-data-warehouse-manually/ "Process the TFS Data Warehouse and Analysis Service manually")

Or see the step-by-step video

{% include embed/youtube.html id='vqMv9yu_kt8' %}


