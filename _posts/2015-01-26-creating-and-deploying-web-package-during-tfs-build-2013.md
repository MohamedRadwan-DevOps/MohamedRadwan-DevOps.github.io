---
layout: post
title: "Creating and Deploying Web Package during TFS Build 2013"
date:   2015-01-26 15:12:33 +0100
---

I have an old post that perform++the same idea++with TFS 2010 but as usual
there are some differences with TFS 2013:-) [How to run remote deploy with MS Deploy](https://mohamedradwan-devops.github.io/posts/how-to-run-remote-deploy-with-ms-deploy/ "Run MSDeploy")

I tried many ways with++many blog posts, they are almost the same but
none of them worked for me, so I decide to create my own solution and
share that include++the Build Process Template, Of course I needed to
install++MSDeploy (Web Deploy 3.5) on the Build machine, [remember how to
install++Web Deployment Agent Service if it\'s not
available](https://mohamedradwan-devops.github.io/2015/08/07/install-missed-web-deployment-agent-service/)

### Customize the process template as the following:

>I didn\'t include error handling during++the customization, you may need to do that :-)
{: .prompt-warning }

-   Adding **ConverWorkspaceItem** and **If** activities, we could
    add++**ConverWorkspaceItem** part of the **If++**sequence, this even
    could be better, you can do that too :-) 
    
     ![ConvertWorkspaceItem and Create packge with Deploy](/assets/img/2015/01/convertworkspaceitem-and-create-packge-with-deploy.png)

-   The **ConverWorkspaceItem** will transform the web application
    selected in the build definition to a local path

    ![ConverWorkspaceItem](/assets/img/2015/01/converworkspaceitem.png)

-   In the **If** activity the main 2 activities are, Create Package
    (**MSBuild** activity) and Deploy Package (**InvokeProcess**
    activity) 
    
    ![Create and Deploy package workflow](/assets/img/2015/01/create-and-deploy-package-workflow.png)

-   The **Create Package** activity will be as the following:
    -   Configuration \-\--\> the configuration that entered in the
        build definition
    -   CommandLineArgument \-\-\--\>/t:build;publish
    -   Project \-\-\--\> the project that transformed from
        **ConverWorkspaceItem** activity

    ![Create Package - MSBuild](/assets/img/2015/01/create-package-msbuild.png)

-   The Deploy Web Package (InvokeProcess)++activity will be as the
    following image: 
    
    ![Deploy Web Package InvokeProcess](/assets/img/2015/01/deploy-web-package-invokeprocess.png)

-   The created package on the working directory on the build agent will
    be as the following: 
    
    ![Web Package](/assets/img/2015/01/web-package.png)

-   The Deployment section on the build definition will be as the
    following:

    ![Dev_Build_Deploy](/assets/img/2015/01/dev_build_deploy.png)

-   How to test the create deployment file on the build agent 
    ![Run file.Deploy.cmd](/assets/img/2015/01/run-file-deploy-cmd.png)

-   How to publish without a package using a publish profile 

    ![Run MSBuild with publish profile](/assets/img/2015/01/run-msbuild-with-publish-profile.png)

-   How to add a parameters value inside the parameter file.xml that
    created with the package 
    
    ![Create Web package and add one paramter in the file](/assets/img/2015/01/create-web-package-and-add-one-paramter-in-the-file.png)

[**Download the process Template**](https://onedrive.live.com/redir?resid=4BCAA16D27B46600!22426&authkey=!AAwD26mHv7T1OrQ&ithint=file%2czip "Download Process Template")

