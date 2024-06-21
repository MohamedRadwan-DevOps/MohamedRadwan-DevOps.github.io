---
layout: post
title:  "How to include minify files or custom files with web package or MS Deploy package?"
date:   2010-11-12 07:40:05 +0100
---

Wow it was a large title any way, I suppose now to sit and finishing my proposal of my Mcs and if the Dr read this article she will tell me, What the hell you are doing?? you should finish your proposal but I couldn\'t prevent my self from writing this post because it\'s very important article to me any way. If you read most of my articles you
will know that I am working on an MVC project and I am using TFS2010 and I automate the whole building process including deployment of database and Test database for Data driven test, running test, deploy database to QA machine and finally create the deploy package and deploy the website to the IIS of the QA machine. I have some issues, I just doing some workarounds until solve it at a proper time, so now the time come for one of the most important issues which is the minify files didn\'t included in the MS deploy package so the deployment of the website
didn\'t deploy this files I read a wonderful article to [sayed.hashimi](http://sedodream.com/2010/03/10/WebDeploymentToolIncludingOtherFiles.aspx "Sayed"), you always impressed me Sayed!! But it needs a little tweaking to work with minify fiels and I found a question on [StackOverFlow](http://stackoverflow.com/questions/4144472/how-can-we-include-the-files-created-by-ajaxmin-in-the-msdeploy-package-created-b "Stack question") which is \"How can we include the files created by ajaxmin in the msdeploy package created by MSBuild \" so I decide to post an article describe my tweaking to solve this issue. 

First you can download the whole project which successfully include the minify file in the MS
Deploy package from here [[**Download**]](/assets/img/2017/08/MvcApplication1.zip "MinifyFilesWithMSDeploy")

First you need to create include for each folder in your application that has minify files and this will has source and destination folder so you make sure you didn\'t copy the minify file in every script folder in your application as the following 

[![SolSolution file that show the scripts in your project](/assets/img/2010/11/12-11-2010.jpg)](/assets/img/2010/11/12-11-2010.jpg)

You need to follow the image or just download the project as mention before

[![MVCProject file.csproj](/assets/img/2010/11/TheProjectFiles.png)](/assets/img/2010/11/TheProjectFiles.png)

You can also see the text version here

```xml
<!-- ======== Minify files ========= -->
<Import Project="$(MSBuildExtensionsPath)MicrosoftMicrosoftAjaxajaxmin.tasks" />
<Target Name="AfterBuild">
    <ItemGroup>
        <JS Include="**/*.js" Exclude="**/*.min.js;Scripts/*.js" />
    </ItemGroup>
    <ItemGroup>
        <CSS Include="**/*.css" Exclude="**/*.min.css" />
    </ItemGroup>
    <AjaxMin JsSourceFiles="@(JS)" JsSourceExtensionPattern=".js$" JsTargetExtension=".min.js" CssSourceFiles="@(CSS)" CssSourceExtensionPattern=".css$" CssTargetExtension=".min.css" />
</Target>

<!-- ====== Package the minify files ===== -->
<PropertyGroup>
    <CopyAllFilesToSingleFolderForPackageDependsOn>
        CustomCollectFiles; $(CopyAllFilesToSingleFolderForPackageDependsOn);
    </CopyAllFilesToSingleFolderForPackageDependsOn>
</PropertyGroup>
<Target Name="CustomCollectFiles">
    <ItemGroup>
        <!-- =====Root folder ==== -->
        <_CustomFilesForRootFolder Include="MyScript/*.min.js">
            <DestinationRelativePath>%(RecursiveDir)%(Filename)%(Extension)</DestinationRelativePath>
        </_CustomFilesForRootFolder>
        <FilesForPackagingFromProject Include="%(_CustomFilesForRootFolder.Identity)">
            <DestinationRelativePath>MyScript%(RecursiveDir)%(Filename)%(Extension)</DestinationRelativePath>
        </FilesForPackagingFromProject>
        <!-- ======sub folder ==== -->
        <_CustomFilesForSubFolder1 Include="MyScriptLogin/*.min.js">
            <DestinationRelativePath>%(RecursiveDir)%(Filename)%(Extension)</DestinationRelativePath>
        </_CustomFilesForSubFolder1>
        <FilesForPackagingFromProject Include="%(_CustomFilesForSubFolder1.Identity)">
            <DestinationRelativePath>MyScriptLogin%(RecursiveDir)%(Filename)%(Extension)</DestinationRelativePath>
        </FilesForPackagingFromProject>
        <!-- === another sub folder ==== -->
        <_CustomFilesForSubFolder2 Include="MyScriptRegistration/*.min.js">
            <DestinationRelativePath>%(RecursiveDir)%(Filename)%(Extension)</DestinationRelativePath>
        </_CustomFilesForSubFolder2>
        <FilesForPackagingFromProject Include="%(_CustomFilesForSubFolder2.Identity)">
            <DestinationRelativePath>MyScriptRegistration%(RecursiveDir)%(Filename)%(Extension)</DestinationRelativePath>
        </FilesForPackagingFromProject>
    </ItemGroup>
</Target>
\</FilesForPackagingFromProject\> \</ItemGroup\> \</Target\>
```

That\'s it

