---
layout: post
title: "Versioning Assembly during TFS Build 2013"
date: 2015-01-27 14:44:25 +0100
---

My fellow MVPs [Colin Dembovsky](http://www.colinsalmcorner.com/about) and [Ricci Gian Maria](http://www.codewrecks.com/blog/) had great posts on doing Assembly Versioning. It doesn’t cover my case but they helped me very well. Thanks, guys :-) 

First, it’s better to understand the Assembly version. Assembly versions consist of four different parts ({**Major** Version}.{**Minor** Version}.{**Build** Number}.{**Revision** Source Control Revision}) **Major**.**Minor**.**Build**.**Revision** 

**Major**: The main version of the product. For example, the Major of all the VisualStudio 2012 assemblies is 11 and VisualStudio 2013 are 12. 

**Minor**: Small changes that don’t require changing in Application interfaces, so it will not break other applications it depends on. This number will be reset to zero when the Major number changes. 

**Build**: Using this number you can find the build on the build server. 

**Revision**: This is the number from source control for that build number. See the following image:

![VS Version](/assets/images/2015/01/vs-version.png?w=660)

**We can see in the previous image that the Version is different from the File Version? So why does this happen?** To answer this question we need to know that you don’t have to do that, but as the Version is the version that .NET uses when linking assemblies, you might want to keep the Version without the build number and the revision as you may want to change something, it might be only changing in the build parameters and you don’t want to rebuild all dependent assemblies.

**Using one AssemblyInfo.cs for all projects within the same solution** We might want to use one file to maintain the Version and the File version for all projects as the following:

- Create AssemblyInfo.cs as a solution file, it will include AssemblyVersion and AssemblyFileVersion attributes
- Add an existing item for all your projects as a linked item to point to that file
- Remove the AssemblyVersion and AssemblyFileVersion attributes from all the project AssemblyInfo.cs files.

![Add exiting item as link](/assets/images/2015/01/add-exiting-item-as-link.png?w=660)

**Versioning Assembly during TFS Build** The idea here is to change the number in the AssemblyInfo.cs during the build and before the compiling happens. In my case, I use a PowerShell script and I customize my process as follows:

```powershell
Param(
    [string]$pathToSearch,
    [string]$buildNumIncludeBuildDefination,
    [string]$extractedBuildNum,
    [string]$chagesetWithC,
    [string]$chageset,
    [string]$searchFilter = "AssemblyInfo*.*",
    [string]$assemblyVersion,
    [string]$fileAssemblyVersion
)

try {
    $extractedBuildNum = $buildNumIncludeBuildDefination.substring($buildNumIncludeBuildDefination.LastIndexOf(".")+1 ,(($buildNumIncludeBuildDefination.length)- ($buildNumIncludeBuildDefination.LastIndexOf("."))-1))
    $chageset = $chagesetWithC.substring($chagesetWithC.LastIndexOf("C")+1 ,(($chagesetWithC.length)- ($chagesetWithC.LastIndexOf("C"))-1))
    $assemblyVersion = $assemblyVersion.Replace("B", $extractedBuildNum).Replace("R", $chageset)
    $fileAssemblyVersion = $fileAssemblyVersion.Replace("B", $extractedBuildNum).Replace("R", $chageset)

    gci -Path $pathToSearch -Filter $searchFilter -Recurse | %{
        Write-Host " -> Changing $($_.FullName)"
        # remove the read-only bit on the file
        sp $_.FullName IsReadOnly $false
        # run the regex replace
        (gc $_.FullName) | % { $_ -replace 'AssemblyVersion("[0-9]+(.([0-9]+|*)){1,3}")', "AssemblyVersion(""$assemblyVersion"")" }| sc $_.FullName
        (gc $_.FullName) | % { $_ -replace 'AssemblyFileVersion("[0-9]+(.([0-9]+|*)){1,3}")', "AssemblyFileVersion(""$fileAssemblyVersion"")" }| sc $_.FullName
        Write-Host "Done!"
        Write-Host $assemblyVersion
        Write-Host $fileAssemblyVersion
        Write-Host $extractedBuildNum
    }
} catch {
    Write-Host $_
    exit 1
}
```

I opened the process template and within **"Try Compile and Test"** I added an **If** sequence activity  
![In Try and Compile I add if sequence](/assets/images/2015/01/in-try-and-compile-i-add-if-squence.png)

The main activity inside the "If" activity will be **InvokeProcess** as follows:  
![VersionAssembly InvokeProcess](/assets/images/2015/01/versionassembly-invokeprocess.png?w=660)

I sent arguments to the PowerShell script as follows:  
![Argument for PowerShell](/assets/images/2015/01/argument-for-powershell.png?w=660)

To set parameters in the build definition, see the following image:  
![Dev_Build_Version](/assets/images/2015/01/dev_build_version1.png?w=660)

Remember if you want to not change the Version number, remove B.R and Add 0.0 instead ex (2.5.0.0)

[Download the Process Template](https://onedrive.live.com/redir?resid=4BCAA16D27B46600!22426&authkey=!AAwD26mHv7T1OrQ&ithint=file%2czip "Download the Process Template")

[Download PowerShell Script](https://onedrive.live.com/redir?resid=4BCAA16D27B46600!22429&authkey=!AHGC6cOE0h3eQLc&ithint=file%2czip)


