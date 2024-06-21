---
layout: post
title: "Install SharePoint 2010 with MS SQL Server 2012 on Windows Server 2012"
date:   2012-06-21 16:29:05 +0100
---

When I start my journey of installing [Team Foundation Server 2012
(TFS)](http://msdn.microsoft.com/library/tfs) on
[Windows Server 2012](http://www.microsoft.com/en-us/server-cloud/windows-server/2012-default.aspx)
with [MS SQL 2012](http://www.microsoft.com/sqlserver/en/us/default.aspx),
I knew that we can\'t install [SharePoint Foundation 2010](http://sharepoint.microsoft.com/en-us/product/Related-Technologies/Pages/SharePoint-Foundation.aspx)
on [Windows Server 2012](http://www.microsoft.com/en-us/server-cloud/windows-server/2012-default.aspx),
this by design and sure the [Team Foundation Server (TFS)](http://msdn.microsoft.com/library/tfs)
standard configuration will not be able to do that :-(

And if we want to install [SharePoint Server 2010](http://technet.microsoft.com/en-us/library/cc303422.aspx)
with [Team Foundation Server (TFS)](http://msdn.microsoft.com/library/tfs) 2012 we
have 2 options

1.  Use [Windows 2008 R2](http://www.microsoft.com/en-us/server-cloud/windows-server/default.aspx)
    so we can install [SharePoint 2010 Foundation](http://sharepoint.microsoft.com/en-us/product/Related-Technologies/Pages/SharePoint-Foundation.aspx)
2.  Use [SharePoint Server 2010](http://technet.microsoft.com/en-us/library/cc303422.aspx)  so
    we can be able to install it on [Windows Server 2012](http://www.microsoft.com/en-us/server-cloud/windows-server/2012-default.aspx)

So I try to install SharePoint prerequisites but it fails and give me
the following error

> [There was an error during installation.]
>
> [The tool was unable to install Application Server Role. Web Server
> (IIS) Role. configuration
> error, installation skipped]

This happen for many reason, for example most of the prerequeist not
supported for Windows Server 2012 because some of them become part of
the Windows Server 2012 and some of them become par of the MS SQL 2012
as we will see later in this post.\
So I try to install SharePoint and skip the prerequiest  and I found the
following errors

> [This product requires the windows identity
> foundation]\
> [This product requires Microsoft Sync Framework Runtime
> v1.0(x64)]\
> [This product requires Microsoft SQL Server 2008 Native Client.
> Install SQL Server 2008 Native Client and re-run
> setup.]\
> [Windows Features or Role Service required by this product are not
> enabled. For a complete list, refer to the link
> below.]\
> [This product requires Microsoft Filter pack
> 2.0]\
> [This product requires internet information services (IIS) 7.0 or
> higher, with ASP \>NET v2.0 set to \'Allow\' in the list of IIS Web
> Server Extensions.]\
> [This product requires the IIS 6 Management Compatibility component to
> install]\
> [This product requires Microsoft Chart Controls for Microsoft .NET
> Framework 3.5 to be installed.]
>
> [For more info about MS SQL Server
> 2012](http://blogs.msdn.com/b/data-platform/?ocid=soc-n-eg-elite--MRadwan)
>
> [For more info about Windows Server 2012](http://blogs.technet.com/b/windowsserver/?ocid=soc-n-eg-elite--MRadwan)

So [Windows Identity Foundation](http://msdn.microsoft.com/en-us/security/aa570351.aspx) become
a Windows Server 2012 Role, so we just enable this Role on Windows 2012
Server

[![](/assets/img/2012/06/0.png "0")](/assets/img/2012/06/0.png)

Also the Reporting Service SharePoint add-in become a component in MS
SQL Server 2012

[![](/assets/img/2012/07/00-1.png "00")](/assets/img/2012/07/00-1.png)

[Note: Only SharePoint 2010 SP1 supported for MS SQL Server 2012 and
even if the installation success without SP1 the configuration will
fail.]

So the steps to install SharePoint 2010 Server on Windows Server 2012
with MS SQL Server 2012 will be as the following

-   Install MS SQL 2012 with SharePoint add-in
-   Configure some Windows 2012 Roles and Features manually
-   Return specific Environment.Exit code
-   Run SharePoint 2010 prerequiest  and install them from SharePoint
    2010 Server SP1 (Only SharePoint 2010 SP1 support MS SQL Server2012)
-   Install SharePoint 2010 Server SP1
-   Set the default app pool to v 2.0 instead of 4.0 because this what
    SharePoint 2010 needs
-   Configure SharePoint 2010
-   provision the installation and configuration



**Note**: you may want to setup SharePoint 2010 with SQL Server 2012 on
Windows Server 2008 R2, it\'s OK, you can follow the same steps.



Here is the video of the installation

{% include embed/youtube.html id='kN0p51S85YI' %}


### If you prefer to follow steps with screen shots, review the following steps

-   Install [MS SQL 2012 with Reporting Service for SharePoint add-in](http://www.microsoft.com/en-us/download/details.aspx?id=29068)



[![](/assets/img/2012/06/sql1.jpg "sql1")](/assets/img/2012/06/sql1.jpg)


[![](/assets/img/2012/06/sql2.png "sql2")](/assets/img/2012/06/sql2.png)


[![](/assets/img/2012/06/sql3.png "sql3")](/assets/img/2012/06/sql3.png)



[![](/assets/img/2012/06/sql4.png "sql4")](/assets/img/2012/06/sql4.png)


[![](/assets/img/2012/06/sql5.png "sql5")](/assets/img/2012/06/sql5.png)



[![](/assets/img/2012/06/sql7.png "sql7")](/assets/img/2012/06/sql7.png)


[![](/assets/img/2012/06/sql8.png "sql8")](/assets/img/2012/06/sql8.png)



[![](/assets/img/2012/06/sql9.png "sql9")](/assets/img/2012/06/sql9.png)


[![](/assets/img/2012/06/sql10.png "sql10")](/assets/img/2012/06/sql10.png)



-   Configure some Windows 2012 Roles and Features manually

We will choose 2 Roles and 1 feature and for each Role we will choose
it\'s features and so the feature, we will choose it\'s components


-   Web IIS (Role)
-   Application Server (Role)
-   Windows Identity Foundation 3.5 (Feature)



[![Add Roles and Features Windows
2012](/assets/img/2012/06/1.jpg "Add Roles and Features Windows 2012")](/assets/img/2012/06/1.jpg)

 


[![Installation Type Role and Feature widows Server 2012](/assets/img/2012/06/2.jpg "Installation Type Role and Feature widows Server 2012 ")](/assets/img/2012/06/2.jpg)






[![Server Selection Windows Server 2012](/assets/img/2012/06/3.jpg "Server Selection Windows Server 2012")](/assets/img/2012/06/3.jpg)




[![Server Roles Windows Server 2012](/assets/img/2012/06/4.jpg "Server Roles Windows Server 2012")](/assets/img/2012/06/4.jpg)


[![](/assets/img/2012/06/5.jpg "Add Role and Feature Wizard Management Tool Windows Server 2012")](/assets/img/2012/06/5.jpg)




[![Server Roles Application Server Windows Server 2012](/assets/img/2012/06/6.jpg "Server Roles Application Server Windows Server 2012")](/assets/img/2012/06/6.jpg)


[![Feature Windows Identify Foundation 3.5](/assets/img/2012/06/7.jpg "Feature Windows Identify Foundation 3.5")](/assets/img/2012/06/7.jpg)


[![Web Server Role- Role Services Health and Diagnostics](/assets/img/2012/06/8.jpg "Web Server Role- Role Services Health and Diagnostics")](/assets/img/2012/06/8.jpg)


[![Web Server Role- Role Services Security](/assets/img/2012/06/9.jpg "Web Server Role- Role Services Security ")](/assets/img/2012/06/9.jpg)





 





 





 





[![Web Server Role- Role Services Application Development](/assets/img/2012/06/10.jpg "Web Server Role- Role Services Application Development")](/assets/img/2012/06/10.jpg)



[![Add Roles and Features Wizard Application Development](/assets/img/2012/06/11.jpg "Add Roles and Features Wizard Application Development")](/assets/img/2012/06/11.jpg)


[![Add Roles and Features Wizard ASP](/assets/img/2012/06/12.jpg "Add Roles and Features Wizard ASP")](/assets/img/2012/06/12.jpg)



[![Add Roles and Features Wizards ISAPI Extensions](/assets/img/2012/06/13.jpg "Add Roles and Features Wizards ISAPI Extensions")](/assets/img/2012/06/13.jpg)

[![Web Server Role- Role Services ASP.NET 3.5](/assets/img/2012/06/14.jpg "Web Server Role- Role Services ASP.NET 3.5")](/assets/img/2012/06/14.jpg)





[![Add Roles and Features- ISAPI Filters](/assets/img/2012/06/15.jpg "Add Roles and Features- ISAPI Filters")](/assets/img/2012/06/15.jpg)


[![](/assets/img/2012/06/16.jpg "Web Server Role- Role Services- CGI and Management Tools")](/assets/img/2012/06/16.jpg)


[![Web Server Role- Role Services Management Console](/assets/img/2012/06/17.jpg "Web Server Role- Role Services Management Console")](/assets/img/2012/06/17.jpg)




[![Add Roles and Features -II6 WMI Compatibility](/assets/img/2012/06/18.jpg "Add Roles and Features -II6 WMI Compatibility ")](/assets/img/2012/06/18.jpg)





 




[![Web Server Role- Role Service Scripting Tools](/assets/img/2012/06/19.jpg "Web Server Role- Role Service Scripting Tools")](/assets/img/2012/06/19.jpg)





 





 





 





[![Application Server-Role Services Distributed Transactions](/assets/img/2012/06/20.jpg "Application Server-Role Services Distributed Transactions")](/assets/img/2012/06/20.jpg)




[![Add Roles and Features ASP.NET 4.5](/assets/img/2012/06/21.jpg "Add Roles and Features ASP.NET 4.5")](/assets/img/2012/06/21.jpg)


[![Application Server-Role Services TCP Activation](/assets/img/2012/06/22.jpg "Application Server-Role Services TCP Activation")](/assets/img/2012/06/22.jpg)





 





 





 





[![Application Server-Role Services Windows Process Activation](/assets/img/2012/06/23.jpg "Application Server-Role Services Windows Process Activation")](/assets/img/2012/06/23.jpg)





 





 





[![Install Windows Server 2012 Roles and Features](/assets/img/2012/06/install-windows-server-2012-roles-and-features.png "Install Windows Server 2012 Roles and Features")](/assets/img/2012/06/install-windows-server-2012-roles-and-features.png)



-   Return specific Environment.Exit code


We will just give installation what it need, it just check for exist
code 1003 so we will give this to SharePoint installation app, this was
provided by
[Steve](http://blog.hand-net.com/sharepoint/2010-06-10-error-lors-de-linstallation-des-office-web-apps-2010-sur-windows-7.htm "Steve"),
well done Steve, its really helpful, so we will download the exe or just
compile the source and put it in System32 Folder


-   Run SharePoint 2010 prerequiest  and install them from SharePoint
    2010 Server SP1 (Only SharePoint 2010 SP1 support MS SQL Server2012)

[![Install SharePoint 2010 Prerequisites](/assets/img/2012/06/24.jpg "Install SharePoint 2010 Prerequisites")](/assets/img/2012/06/24.jpg)



[![Microsoft SharePoint 2010 Product Preparation Tool](/assets/img/2012/06/25.jpg "Microsoft SharePoint 2010 Product Preparation Tool")](/assets/img/2012/06/25.jpg)



[![Configure Application Server Role - Web Server (IIS) Role](/assets/img/2012/06/26.jpg "Configure Application Server Role - Web Server (IIS) Role")](/assets/img/2012/06/26.jpg)



[![SharePoint 2010 Product Preparation Tool Installation Complete](/assets/img/2012/06/27.jpg "SharePoint 2010 Product Preparation Tool Installation Complete")](/assets/img/2012/06/27.jpg)


-   Install SharePoint 2010 Server SP1


[![Install SharePoint 2010 SP1](/assets/img/2012/06/29.jpg "Install SharePoint 2010 SP1")](/assets/img/2012/06/29.jpg)


[![SharePoint 2010 Accept the terms](/assets/img/2012/06/30.jpg "SharePoint 2010 Accept the terms ")](/assets/img/2012/06/30.jpg)


[![Install SharePoint Complete Server Farm](/assets/img/2012/06/31.jpg "Install SharePoint Complete Server Farm ")](/assets/img/2012/06/31.jpg)


-   Set the default app pool to v 2.0 instead of 4.0 because this what
    SharePoint 2010 needs


[![Open the default app pool](/assets/img/2012/06/42.jpg "Open the default app pool ")](/assets/img/2012/06/42.jpg)



[![Change app pool to .NET Framework version 2.0](/assets/img/2012/06/43.jpg "Change app pool to .NET Framework version 2.0")](/assets/img/2012/06/43.jpg)



If we didn\'t set this the configuration will fail as the following

[![SharePoint Products Configuration Wizard Configuration Failed](/assets/img/2012/06/37.jpg "SharePoint Products Configuration Wizard Configuration Failed")](/assets/img/2012/06/37.jpg)


If this happen we will need to the change the app pool for crated
pools related to SharePoint, after SharePoint configuration failed



[![Change the Application Pool Runtime](/assets/img/2012/06/38.jpg "Change the Application Pool Runtime")](/assets/img/2012/06/38.jpg)


[![Change the Application Pool Runtime](/assets/img/2012/06/39.jpg "Change the Application Pool Runtime")](/assets/img/2012/06/39.jpg)



Start SharePoint CA

![Set Application Pool Default to v 2.0 instead of v4.0](/assets/img/2012/06/40.jpg "Set Application Pool Default to v 2.0 instead of v 4.0")




-   Configure SharePoint 2010

[![Create New Server Farm](/assets/img/2012/06/32.jpg "Create New Server Farm")](/assets/img/2012/06/32.jpg)



[![Create a new Server Farm](/assets/img/2012/06/32.jpg "Create a new Server Farm")](/assets/img/2012/06/32.jpg)


[![Specify Configuration Database settings](/assets/img/2012/06/33.jpg "Specify Configuration Database settings")](/assets/img/2012/06/33.jpg)




[![Configure SharePoint Center Administration Web Application set port number](/assets/img/2012/06/34.jpg "Configure SharePoint Center Administration Web Application set port number")](/assets/img/2012/06/34.jpg)







[![Completing the SharePoint Products Configuration Wizard](/assets/img/2012/06/35.jpg "Completing the SharePoint Products Configuration Wizard ")](/assets/img/2012/06/35.jpg)

 





[![Configure SharePoint Products](/assets/img/2012/06/36.jpg "Configure SharePoint Products ")](/assets/img/2012/06/36.jpg)








[![SharePoint Product Configuration Wizard Configuration Successful](/assets/img/2012/06/44.jpg "SharePoint Product Configuration Wizard Configuration Successful ")](/assets/img/2012/06/44.jpg)




-   provision the installation and configuration, just open CA

[![Open SharePoint Center Administration](/assets/img/2012/06/41.jpg "Open SharePoint Center Administration ")](/assets/img/2012/06/41.jpg)

