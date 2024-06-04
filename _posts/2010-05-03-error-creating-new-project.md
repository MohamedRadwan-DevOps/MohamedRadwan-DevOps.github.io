---
layout: post
title:  "Error TF218017 when you Creating New Team Project TFS2010"
date:   2010-05-03 07:40:05 +0100
---

Today I start create a new Team project on my new TFS 2010 and I face the following error. TF218017: A SharePoint site could not be created for use as the team project portal. The following error ocurred: TF250044: A SharePoint site cannot be created at the following location: "yourLocation" The following user account does not have the required permissions in SharePoint Products to create a site at that location: "yourLocation" The user account must have sufficient permissions to create a sub-site on the following site: "yourLocation" 

[![error](/assets/images/2010/05/error.jpg)](/assets/images/2010/05/error.jpg) 

I worked with TFS since 2005 and I used to follow the installation guide, and that's what I did, but I don't know why I got this error despite of blind following  the installation guide, anyway this error mean that the account that try to create the sharepoint portal for your project doesn't have permission to create it, so I solve it as the following I login to my machine using local account  called mradwan and of curse this account existing on the TFS2010 server because I used workgroup approach for various reasons not important now, so All I have to do is to go to the TFS2010 server and start add mradwan account to the site administrator of the sites of the TFS2010 as the following 

[![WSSApplicationManagement](/assets/images/2010/05/WSSApplicationManagement.png)](/assets/images/2010/05/WSSApplicationManagement.png) 

[![AddMyAccount](/assets/images/2010/05/AddMyAccount.png)](/assets/images/2010/05/AddMyAccount.png) 

Of curse sometimes this is not the only reasons for error TF218017 as we used too :) so if this the case you can keep search of the error and maybe this link could help you [MSDN Forum](http://social.msdn.microsoft.com/Forums/en-US/tfsadmin/thread/78c467a5-d163-4bc7-b02b-24f9147e182c "Error") [The error with beta version](http://www.sathishtk.com/blog/post/2009/11/20/SharePoint-2010-Beta-2-and-Team-Foundation-Server-%28TFS%29-2010-Beta-2-Integration.aspx "error")