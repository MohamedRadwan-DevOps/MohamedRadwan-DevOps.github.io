---
layout: post
title: "Solve the MVC 3 Shortcut conflict with MVC 2 on Visual Studio 2010"
date:   2011-10-10 08:19:34 +0100
---

When we install MVC 3 on Visual Studio 2010, the shortcut for MVC 3
didn\'t work and this because all shortcut are associated with MVC 2, we
can solve this issue by many ways, We can
open\--\>Tool\--\>Option\--\>Enviroment\--\>Keyboard Start search for
the following items, and we will found each one has 2 items, so we will
associate shortcut to the item that didn\'t has:

-   ProjectandSolutionContextMenus.Project.Add.Controller Ctrl+M, Ctrl+C
-   ProjectandSolutionContextMenus.Project.Add.Area     Ctrl+M, Ctrl+A
-   EditorContextMenus.CodeWindow.AddView     Ctrl+M, Ctrl+V
-   OtherContextMenus.ASPXcontext.GoToController    Ctrl+M, Ctrl+G
-   Project.AddClass     SHIFT+ALT+C

We can also make another solution by removing MVC 2 Tool from Add
Remove Program but this will make any existing MVC 2 application not be
able to work, if you remove it by mistake you can install this tool
again from VS2010 DVD, the tool name is VS2010ToolsMVC2.msi and can be
fond  under WCUASPNETMVC

[![](/assets/img/2011/10/Remove-MVC-2-1024x569.png)](/assets/img/2011/10/Remove-MVC-2.png)

