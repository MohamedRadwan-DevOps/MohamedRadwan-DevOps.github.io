---
layout: post
title: "Complete the virtual machine after you create your environment in Lab Management"
date:   2011-06-17 10:58:43 +0100
---

After I create the enviroment

-   Join any machine to the domain
-   Add TFSLAB as local admin for all machine that has build agent
    (becaue Builg Agent configuration) (I will not use TFSBUILD since
    the build agent just need to deploy not to compile so we don\'t need
    account access the source control)
-   Configure the Test Agent ( using TFSLAB) for each machine depend on
    the machine (Client\-\--\> interactive process, Server\--\> service)
-   Configure the build Agent ( using TFSLAB)
-   Refresh your environment
-   it should work now

