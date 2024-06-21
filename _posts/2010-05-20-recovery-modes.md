---
layout: post
title:  "Recovery mode for MS SQL Server 2008"
date:   2010-05-20 07:40:05 +0100
---

I started today deploy a CMS project "Umbraco" to a shared hosting, I prefer to use my favorite tool VSTS 2008 DB professional, I face a big problem when I compare data and try to write the update,  the error happens because the log  is expanding and reach the max size so I search for how can I  fix this problem and I find a good information regarding the log file. First we have to understand what the log do in the transaction, if we see the following Pic 

[![](/assets/img/2010/05/log-opreation.jpg?w=300 "Log operation")](/assets/img/2010/05/log-opreation.jpg) 

So we can see that for example in the previous pic we have an account that we want to update by withdraw 50$ from it so the log will capture the record before and after the update and guess why he doing that? that's right because in case of you want to rollback or disaster recovery if there something happen to your records. You have to notice that there 3 option exist in MS SQL server for log option and they called recovery option, you can change the recovery mode as the following 

[![](/assets/img/2010/05/recovery-model.jpg?w=300 "Recovery model")](/assets/img/2010/05/recovery-model.jpg) 

Or you can change it by running the following query ALTER DATABASE DBName SET RECOVERY Bulk\_logged You can check for the recovery mode by running the following query SELECT name, recovery\_model, recovery\_model\_desc from master.sys.databases 

[![](/assets/img/2010/05/recovery-model-result.jpg?w=300 "Recovery model Result")](/assets/img/2010/05/recovery-model-result.jpg) 

This will affect the log size, and of course the ability of recovery of the data.

