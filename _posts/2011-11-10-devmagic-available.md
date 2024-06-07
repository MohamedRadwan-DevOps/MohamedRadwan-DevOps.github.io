---
layout: post
title: "DevMagicFake Code Snippet now available"
date:   2011-11-10 05:11:32 +0100
---

I just create 2 snippets not only for DevMagicFake but for any faking code that may I write throughout the project life cycle, I also will add rule to my development rules guidance that it\'sprohibitedto write any
faking codeoutsidethe faking area, this will allow us to track back
all faking code. There is also a workaround snippet that
willsurroundall workarounds that approved as workarounds and they have
referenceto the issue thatrecordedon the issue system, it will be add
also to my rules guidance as well. At any point of time you can look
attechnologydepts as workarounds and surround it with workaround
snippet to bere-factorand paid later in thenearestchance, we can
download thesnippetinstaller (msi) just go to the CodePlex download
page and download it for click on
thefollowinglink:

[download](https://github.com/DevOpsFounder/Dev-Magic-Fake/blob/master/misc/DevMagicFakeSnippet.msi "Download snippets")

```csharp
// REMOVEFAKE: FakeNote
// BeginFaking
// My fake code here
// EndFaking
```

```csharp
// REMOVEWORKAROUND: IssueNumber250
// Beginworkaround
// My workaround here
// Endworkaround
```


\[sourcecode language=\"csharp\"\] //REMOVEFAKE:FakeNote
//BeginFaking //Myfakecodehere //EndFaking \[/sourcecode\]
\[sourcecode language=\"csharp\"\] //REMOVEWORKAROUND:IssueNumber250
//Beginworkaround //My workaroundhere //Endworkaround
\[/sourcecode\] 

To make thesesnippets effective we will need to add 2 task tokens to the task list in Visual Studio as the following:

[![](/assets/images/2011/11/TaskListTokens.png)](/assets/images/2011/11/TaskListTokens.png)

Now we can go to any faking or workaround code, and we are sure that
all ourdebtsarerecordedin amannerthat we can veryeasilyand
quicklytrack them back :-)

