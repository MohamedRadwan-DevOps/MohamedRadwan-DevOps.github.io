---
layout: post
title: "LabCenter can't feel the SCVMM as it's not configured"
date:   2011-06-29 20:45:32 +0100
---

Finally after completing my infrastructure and start to use it, when I
access the Lab center it doesn\'t work and give me a gray message that
said \"the Lab Management maybe not configure\"  when I check this error
I found the following: When I open the TFS Admin console and open the
Lab Management node and click reconfigure and test the name of the SCVMM
it give me an error I do many things but the problem was not normal the
problem that when the TFS machine lose the domain trust of the active
directory this happen I face also the following errors: \"[Team
Foundation Server cannot contact the following Virtual Machine
Manager]\" \"[The following library share could
not be verified because of one or more errors: name: \'[name\'
path]: \'\\[network
path]\' . Possible causes include: a) the
library server is currently unavailable, or b) the library share was
deleted, renamed, or removed and added back in SCVMM. Delete this
library share from project collection, close the dialog, reopen it, and
then add it again to project collection].\" So I
do the following

-   Uninstall SCVMM from the hyper v machine and deleted it\'s database
-   You may need to un-join and rejoin the domain again for the hyper v
    machine
-   You may need also to un-join and rejoin the domain again for the TFS
    machine
-   You may need to create a library and make it as network share first
    and give the TFSSERVICE read and write permission on it
-   Try to verify the library from the TFS Admin console in the
    application tier node
-   If it\'s not verified you will need to add new library from SCVMM
    Admin by adding folder and share and give TFSSERVICE Read/write
    share permission after that you can delete the default library
    folder and re add it again, but remember you can\'t delete library
    from Team collection unless you put another one

For some little help see the following page
[http://msdn.microsoft.com/ru-ru/library/ff966328.aspx](http://msdn.microsoft.com/ru-ru/library/ff966328.aspx "Lab management error")

