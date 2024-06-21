---
layout: post
title: "Debugging TFS Job Agent Extension"
date: 2014-11-14 16:00:51 +0100
---

Creating a TFS Job Agent was not difficult at all, but debugging it was a pain in the neck! :-) Here I explain how to find what the error is and how to fix it.

## [Extension not found for TFSJobAgent (ExtensionNotFound)]{style="color: #ff0000;"}

So first, how to know if my job agent succeeded or failed, and if it failed, why did this happen?

**How to see this**: Open the following link: [http://TFSServer:8080/tfs/_oi/] Click on the job history. If the job failed, you will see it here, and you can click on the small arrow to see History or Definition.

![TFS Job Definition and History](/assets/img/2014/11/tfs-job-definition-and-history1.png)

**History**  
![TFS Job History Details](/assets/img/2014/11/tfs-job-history-details.png)

**Definition**  
![TFS Job Definition Details](/assets/img/2014/11/tfs-job-definition-details.png)

In case there is nothing in the history, you should see your job on the Job Monitoring page as the following:

![TFS Job Monitoring](/assets/img/2014/11/tfs-job-monitoring.png)

Remember you will need to restart the TFS Job Agent every time you deploy a new version of the DLL so the service can load the assembly, and this is the reason for the failure the first time.

![Restart TFS Job Agent](/assets/img/2014/11/restart-tfs-job-agent.png)

**Links**:
- [How to see activity and job history in TFS 2012](http://blogs.msdn.com/b/buckh/archive/2013/03/30/how-to-see-activity-and-job-history-in-tfs-2012.aspx)
- [TFS2012: New tools for TFS Administrators](http://blogs.msdn.com/b/granth/archive/2013/02/13/tfs2012-new-tools-for-tfs-administrators.aspx "TFS2012: New tools for TFS Administrators")
- [Identity Synchronization in Team Foundation Server 2010](http://blogs.msdn.com/b/vasu_sankaran/archive/2010/06/07/identity-synchronization-in-team-foundation-server-2010.aspx "Identity Synchronization in Team Foundation Server 2010")
