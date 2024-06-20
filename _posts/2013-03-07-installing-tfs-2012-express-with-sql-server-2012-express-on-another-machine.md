
---
layout: post
title: "Installing TFS 2012 Express with SQL Server 2012 Express on Another Machine"
date: 2013-03-07 01:41:17 +0100
---

Four months ago, [Buck Hodges](http://blogs.msdn.com/b/buckh/archive/2012/11/29/doc-on-unattended-configuration-of-tfs-2012.aspx "Buck Hodges") from the VS ALM team announced a [white paper](http://www.microsoft.com/en-us/download/details.aspx?id=35820 "Unattended Installation of TFS 2012") about how to use *[tfsconfigure unattend command line]{style="color:#0000ff;"}* tool to silently configure TFS 2012. This tool gives the ability to configure TFS 2012 from the command line with all predefined configurations.

Today, I am going to explain how to use this great tool to help me install TFS 2012 Express on a machine and use SQL Server 2012 Express that is already installed on another machine. In my scenario, I have 2 machines: PC1 (TFS 2012) and PC2 (SQL Server Express).

![Architecture](/assets/images/2013/03/architecture-1.jpg)

After installing TFS 2012 Express on PC1 and SQL Server 2012 Express on PC2, I will not configure TFS and perform the following steps:

1. Log in to PC2 with an Admin account and make sure that the SQL Server option "Allow remote connections to this server" is enabled.
   
   ![Allow remote connections to this server is enabled](/assets/images/2013/03/allow-remote-connections-to-this-server-is-enabled-1.png)

2. Open SQL Server Configuration Manager and make sure that TCP/IP Protocols is enabled for SQL Express.
   
   ![TCP-IP Protocols Enabled for SQL Express](/assets/images/2013/03/tcp-ip-protocols-enabled-for-sql-express-1.png)

3. Log in to PC1 with an Admin account that has permission on the SQL machine so it can install the DB there. It's better if you use a Domain Controller account.

4. Open the command line for Visual Studio as an administrator.

5. Navigate to:
   
   ```bash
   cd "C:\Program Files\Microsoft Team Foundation Server 11.0\Tools"

From the command line run the following command:

```bash
tfsconfig unattend /configure /type:basic /inputs:SqlInstance=PC2\TFSSQLExpress
```


**PC2**: is the second machine. 
**TFSSQLExpress**: is the instance name.

Make sure that configuration succeed.

![Configuration Succeed](/assets/images/2013/03/configuration-succeed.png?w=660)


