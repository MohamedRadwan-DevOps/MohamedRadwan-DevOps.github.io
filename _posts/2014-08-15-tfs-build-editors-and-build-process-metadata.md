---
layout: post
title: "TFS Build Editors and Build Process Metadata"
date: 2014-08-15 14:53:57 +0100
---

When we perform customization for the build process, we may add some arguments that can be set by editing the build definition. In some cases, the string data type for an argument will be sufficient, but in other cases, it's not. How about if we want to browse for a file on the source control or if we want to set some settings, etc.? This is why it's important to know that there are built-in editors and we can develop our own editor as well.

**File / Folder Browsing**

| **Function**          | **Class, Assembly**                                                                                     |
|-----------------------|---------------------------------------------------------------------------------------------------------|
| Server folder browser | Microsoft.TeamFoundation.Build.Controls.ServerFolderBrowserEditor, Microsoft.TeamFoundation.Build.Controls |
| Server file browser   | Microsoft.TeamFoundation.Build.Controls.ServerFileBrowserEditor, Microsoft.TeamFoundation.Build.Controls   |
| Local folder browser* | System.Windows.Forms.Design.FolderNameEditor, System.Design                                             |
| Local file browser*   | System.Windows.Forms.Design.FileNameEditor, System.Design                                               |

**TFS Build Related Editors**

| **Function**                  | **Class, Assembly**                                                                                             |
|-------------------------------|-----------------------------------------------------------------------------------------------------------------|
| Build Agent selector          | Microsoft.TeamFoundation.Build.Controls.BuildAgentSelectionEditor, Microsoft.TeamFoundation.Build.Controls       |
| Build Number Format Editor    | Microsoft.TeamFoundation.Build.Controls.BuildNumberFormatEditor, Microsoft.TeamFoundation.Build.Controls        |
| Project selector              | Microsoft.TeamFoundation.Build.Controls.BuildProjectListEditor, Microsoft.TeamFoundation.Build.Controls          |
| Build settings                | Microsoft.TeamFoundation.Build.Controls.BuildSettingsEditor, Microsoft.TeamFoundation.Build.Controls             |
| Platform configuration        | Microsoft.TeamFoundation.Build.Controls.PlatformConfigurationListEditor, Microsoft.TeamFoundation.Build.Controls |
| Build Agent Tag               | Microsoft.TeamFoundation.Build.Controls.TagsEditor, Microsoft.TeamFoundation.Build.Controls                      |
| Test specifications           | Microsoft.TeamFoundation.Build.Controls.TestSpecEditor, Microsoft.TeamFoundation.Build.Controls                  |
| Test specification list       | Microsoft.TeamFoundation.Build.Controls.TestSpecListEditor, Microsoft.TeamFoundation.Build.Controls              |
| Work-item type                | Microsoft.TeamFoundation.Build.Controls.WorkItemTypeSelectionEditor, Microsoft.TeamFoundation.Build.Controls     |

**You can create a custom Editor [click here](http://www.ewaldhofman.nl/post/2010/05/17/customize-team-build-2010-e28093-part-6-use-custom-type-for-an-argument.aspx) and here another one [click here](http://blogs.msdn.com/b/jpricket/archive/2010/01/18/tfs-2010-custom-process-parameters-part-3-custom-editors.aspx)** The steps to create a custom one, [click here](http://stackoverflow.com/questions/9275150/tfs-2010-is-it-possible-to-use-a-list-of-key-value-pairs-in-the-processparamete)

**Other Editors**

- Microsoft.TeamFoundation.Build.Controls.dll:
  - Microsoft.TeamFoundation.Build.Controls.EnumPropertyEditor
  - Microsoft.TeamFoundation.Build.Controls.StringListEditor
- System.Design.dll:
  - System.ComponentModel.Design.CollectionEditor
  - System.ComponentModel.Design.BinaryEditor
  - System.ComponentModel.Design.DateTimeEditor
  - System.ComponentModel.Design.MultilineStringEditor
  - System.ComponentModel.Design.ObjectSelectorEditor
  - System.Windows.Forms.Design.FileNameEditor (+)
  - System.Windows.Forms.Design.FolderNameEditor (+)
  - System.Windows.Forms.Design.FormatStringEditor
  - System.Windows.Forms.Design.ImageIndexEditor (??)
  - System.Windows.Forms.Design.LinkAreaEditor
  - System.Windows.Forms.Design.MaskedTextBoxTextEditor
  - System.Windows.Forms.Design.MaskPropertyEditor
  - System.Windows.Forms.Design.ShortcutKeysEditor
  - System.Web.UI.Design.ConnectionStringEditor
  - System.Web.UI.Design.UrlEditor
  - System.Web.UI.Design.XmlFileEditor
  - System.Web.UI.Design.RegexTypeEditor
  - System.Web.UI.Design.SqlDataSourceQueryEditor
- System.Drawing.Design.dll:
  - System.Drawing.Design.ImageEditor
  - System.Drawing.Design.ColorEditor
  - System.Drawing.Design.ContentAlignmentEditor
  - System.Drawing.Design.CursorEditor
  - System.Drawing.Design.FontEditor
  - System.Drawing.Design.FontNameEditor
  - System.Drawing.Design.IconEditor
- System.Workflow.Activities.dll:
  - System.Workflow.Activities.WebServicePickerEditor
  - System.Workflow.Activities.StateDropDownEditor
  - System.Workflow.Activities.ImageBrowserEditor
  - System.Workflow.Activities.LogicalExpressionEditor

For good info about other editors and links, see the following link: [Reusable Editors - TFS build arguments](http://devtfs.wordpress.com/2012/10/23/reusable-editors-tfs-build-arguments/ "Reusable Editors - TFS build arguments")

Good links:

- [http://blogs.microsoft.co.il/oshryhorn/2011/03/22/how-to-use-the-internal-microsoft-custom-ui-type-editors-in-tfs-2010-build-definition/](http://blogs.microsoft.co.il/oshryhorn/2011/03/22/how-to-use-the-internal-microsoft-custom-ui-type-editors-in-tfs-2010-build-definition/)
- [http://blog.jessehouwing.nl/2011/11/which-uieditors-are-available-for-team.html](http://blog.jessehouwing.nl/2011/11/which-uieditors-are-available-for-team.html)
- [http://bartwullems.blogspot.de/2012/07/tfs-build-using-built-in-editors.html](http://bartwullems.blogspot.de/2012/07/tfs-build-using-built-in-editors.html)
- [http://blogs.msdn.com/b/jpricket/archive/2009/12/23/tfs-2010-custom-process-parameters-part-2-metadata.aspx](http://blogs.msdn.com/b/jpricket/archive/2009/12/23/tfs-2010-custom-process-parameters-part-2-metadata.aspx)
- [http://pascoal.net/2011/08/team-foundation-build-enhancing-the-experience-with-built-in-custom-editors/](http://pascoal.net/2011/08/team-foundation-build-enhancing-the-experience-with-built-in-custom-editors/)
- [http://blogs.msdn.com/b/jpricket/archive/2010/01/18/tfs-2010-custom-process-parameters-part-3-custom-editors.aspx](http://blogs.msdn.com/b/jpricket/archive/2010/01/18/tfs-2010-custom-process-parameters-part-3-custom-editors.aspx)
