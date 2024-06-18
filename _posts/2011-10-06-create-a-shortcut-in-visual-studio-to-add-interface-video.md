---
layout: post
title: "Create a shortcut in Visual Studio to add interface video"
date:   2011-10-06 21:01:53 +0100
---

When I try to find a shortcut to add interface to my project, I didn\'t
find, this was very weird to me because I thought sure I can\'t find it
but it\'s there, but when I deeply search I find there is not, so I
decide to post an article on how to do it? See the video

{% include embed/youtube.html id='615y47DWlaE' %}

The code for the Add interface Module as the following: 

```csharp

Public Module AddInterfaceModule
    Sub AddInterface()
        Dim interfaceName As String = Microsoft.VisualBasic.Interaction.InputBox("Name", "Add Interface")
        If Not interfaceName.ToLower().EndsWith(".cs") Then
            interfaceName &= ".cs"
        End If
        DTE.ItemOperations.AddNewItem("Visual C#CodeInterface", interfaceName)
    End Sub
End Module
```

