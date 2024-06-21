---
layout: post
title:  "Why and how to clear TFS client cache?"
date:   2010-06-20 07:40:05 +0100
---

Sometimes there are errors like:

```
\"Cannot find team project\" or you can\'t create a project because
duplicate name  despite of you don\'t have one or you are not connected
to that one that have this project.
```

So all you have to do just clear the cache example of the error that could occur the following error

![CacheError](/assets/img/2010/05/CacheError.png)

For example I clear my cache from the following path [**For Visual Studio
cache:**]

Run from Window Run [%localappdata%] Or open the following path
`[C:UsersMRadwanLocal SettingsApplication DataMicrosoftTeam
Foundation5.0Cache] `

This will cause your client Tool  to download a fresh copy of the cache the next time it deals with
the server, and everything  will going well. We can also force a rebuild
of the cache on **each client computer** the next time it connects to a
team project collection by using the `[witadmin
rebuildcache ]`[**For MTM
cache**]

[C:UsersmradwanAppDataLocalMicrosoftTeamTestv12.0] [**For server cache**] Run from
Window Run [%programdata%] Or open the
following path `[C:ProgramDataMicrosoftTeam FoundationWebAccess]` 
Sometimes also you need to clear the following path `[C:Program FilesMicrosoft Team Foundation Server
12.0Application TierWeb Services_tfs_data]`

Delete the cache files and to make sure we have refreshed everything, we can reset the IIS.  
