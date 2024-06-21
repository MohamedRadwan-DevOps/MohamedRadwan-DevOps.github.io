---
layout: post
title: "Changing the connection string during the TFS build for the Publish Profile of the SSDT (Sql Server Data Tool)"
date: 2015-06-16 07:36:17 +0100
---

One of our customers needed to change that, they needed to type the password for the SQL login inside the publish profile but of course, they couldn't do that for security reasons, so we created that during the TFS build as follows:

- Create a PowerShell script that replaces the connection string.
- Check-In the script into source control.
- Execute the PowerShell script during the build and before compiling the code.

**Create a PowerShell script that replaces the connection string**  
The idea is to create a PowerShell script to search for the publish profile in the build directory on the build machine, then replace the connection string with the one with the password. Remember that we need to do that before compiling the SSDT so during the SSDT deployment, it will use the modified file. During the build, I will send **\$pathToSearch** which will be the build directory, **\$publishProfileString** which will be set as an argument in the build definition, and so **\$sqlUserName** and **\$sqlPassword**.

```powershell
Param(
    [string]$pathToSearch,
    [string]$publishProfileString,
    [string]$sqlUserName,
    [string]$sqlPassword
)
try {
    #$pathToSearch="C:Radwan\"
    #$publishProfileString = "/p:SqlPublishProfilePath=../DAI.Infrastructure.DataAccess.Ef.DbPublishProfiles/DAI.Infrastructure.DataAccess.Ef.Db.preprod.publish.xml"
    #$sqlUserName="vvvvvvvv"
    #$sqlPassword="00000000"
    $publishPostion = $publishProfileString.LastIndexOf("publish.");
    $publishStringWihoutPublish = $publishProfileString.Substring(0, $publishPostion - 1);
    $lastDotPostion = $publishStringWihoutPublish.LastIndexOf(".");
    $publishProfileStageName = $publishStringWihoutPublish.Substring($lastDotPostion+1, $publishStringWihoutPublish.Length - $lastDotPostion-1);
    $searchFilter = "*." + $publishProfileStageName + ".publish.*"
    $replaceValue="User ID=" + $sqlUserName +";password="+$sqlPassword+";"
    gci -Path $pathToSearch -Filter $searchFilter -Recurse | %{
        Write-Host " -> Changing $($_.FullName)"
        # remove the read-only bit on the file
        sp $_.FullName IsReadOnly $false
        # read the file content
        $results = Get-Content $_.PSPath
        Write-Host " -> File content: $($results)"
        # run the regex replace
        #(gc $_.FullName) | % { $_ -replace 'ID=user;', "User ID=""$sqlUserName"";password=""$sqlPassword"";" } | sc $_.FullName
        (gc $_.FullName) | % { $_ -replace 'User ID=user;', $replaceValue } | sc $_.FullName
        Write-Host "Done!"
    }
} catch {
    Write-Host $_
    exit 1
}
```


**Check-In the script into source control** So the script can be downloaded during the build as I will need to run it from the build machine

**Execute the PowerShell script during the build and before compiling the code** 

[![SSDT change connection string](/assets/img/2015/06/ssdt-change-connection-string.png)](/assets/img/2015/06/ssdt-change-connection-string.png)

