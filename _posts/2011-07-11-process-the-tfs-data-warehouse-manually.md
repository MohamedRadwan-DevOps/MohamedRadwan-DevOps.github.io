---
layout: post
title: "Process the TFS Data Warehouse and Analysis Service manually"
date:   2011-07-11 14:31:42 +0100
---

This is a very trivial post but just to remember,

- Open the WarehouseControlService.asmx locally on the TFS machine App tier.
- Click ProcessWarehouse and then click Invoke.
- The service returns True when it successfully starts the processing of the warehouse and False if it is not successful.
- GetProcessingStatus, and then click Invoke.

![TFS_WebServices]( /assets/img/2011/07/TFS_WebServices.jpg)

![IIS_TFS_AppTire PM]( /assets/img/2011/07/IIS_TFS_AppTire-PM.jpg)

![]( /assets/img/2012/08/warehousecontrolwebservice.jpg "WarehouseControlWebService")

![]( /assets/img/2012/08/process-successfuly-invoked.jpg "Process successfully invoked")

Warehouse processing is completed when the GetProcessingStatus service returns a value of Idle for the following jobs:

- Build Warehouse Sync
- Common Structures Warehouse Sync
- Test Management Warehouse Sync
- Version Control Warehouse Sync
- Work Item Tracking Warehouse Sync

After that, process the Analysis Service using the same steps but for the Analysis Service.

![]( /assets/img/2012/08/warehousecontrolwebservice-analysis-service.jpg "WarehouseControlWebService-Analysis Service")

![]( /assets/img/2012/08/invoke-warehousecontrolwebservice-2.jpg "Invoke WarehouseControlWebService 2")

![]( /assets/img/2012/08/process-successfuly-invoked2.jpg "Process successfully invoked 2")

For more information see the following link: [click here](http://msdn.microsoft.com/en-us/library/ff400237.aspx#ProcessWarehouse "MSDN")
