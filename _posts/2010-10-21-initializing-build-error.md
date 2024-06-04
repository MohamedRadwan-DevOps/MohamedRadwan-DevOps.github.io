---
layout: post
title:  "TF215097: An error occurred while initializing a build for build definition.."
date:   2010-10-21 07:40:05 +0100
---

\"TF215097: An error occurred while initializing a build for build
definition yourBuildDef: 

```
There was no endpoint listening at http://tfs2010:9191/Build/v3.0/Services/Controller/1 that could accept the message. This is often caused by an incorrect address or SOAP action. See InnerException, if present, for more details\"

```

This error could occur for many reason of of the way that you could resolved and work with me, go to the TFS Administration console and choose the build and you click start you can also review the event viewer to see the what
cause the error to occur

![TFS Admin Console](/assets/images/2010/10/TFSAdmin.png)

So it become green and working 

![Build working](/assets/images/2010/10/TFSadmin2.png)

That\'s it  
