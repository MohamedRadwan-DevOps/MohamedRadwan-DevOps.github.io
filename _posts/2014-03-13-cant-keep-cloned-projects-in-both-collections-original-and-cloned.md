---
layout: post
title: "Can't keep cloned projects in both collections (original and cloned)"
date:   2014-03-13 14:54:45 +0100
---

Sometimes you may want to clone your collection for many reason, we can
use the following command: 

```xml
C:Program Files\Microsoft Team Foundation Server 12.0\Tools>tfsconfig collection /attach /collectionName:ClonedFabrikam collectionDB:vsalmSQLExpress;TFS_FabrikamFiberCollection /clone
```

And remember:

-   You will need to detach the collection first and make a **copy** of
    the DB
-   The **/clone** switch didn\'t actually clone DB it just telling
    **TFS Admin Console** this is a cloned collection so please don\'t
    start it :-)

**Note 1:** It\'s important to know that you can\'t start the cloned
collection until you delete the projects from the original or the cloned
collection, so you can\'t keep projects on both collection, otherwise
you will face the following error: 

>TF253021:The following team project
is duplicated in at least two team project collections:  The collection
cannot start while the duplication exists. You must delete this project
from all but one of the collections before the collection can be
started. 
{: .prompt-danger }

The project exists in the following collections:


![TF253021](/assets/img/2014/03/tf253021.jpg)

**Note 2:** It\'s Important to know that you must detach the collection
otherwise it will not appear when you try to attach, you can make the
backup without detach if you are making upgrade from old version like
2010 or 2008. 

**Note 3:** For not detached collection you can use

[TFSConfig with Recover](http://blogs.msdn.com/b/tfssetup/archive/2010/09/28/how-to-recover-a-collection-database-when-it-is-not-listed-in-the-tfs-admin-console.aspx "TFSConfig with Recover")

option but this only for TFS2010 but [don\'t use it with TFS2012 or
TFS2013 as it\'s deprecated] Fore more
information:

-   [TFSConfig Collection Command](http://msdn.microsoft.com/en-us/library/ee349263.aspx)
-   [Move a Team Project Collection](http://msdn.microsoft.com/en-us/library/vstudio/dd936138(v=vs.110).aspx)
-   [Split a Team Project Collection](http://msdn.microsoft.com/en-us/library/vstudio/dd936158(v=vs.110).aspx)

