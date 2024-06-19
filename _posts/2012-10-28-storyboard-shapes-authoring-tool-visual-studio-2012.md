---
layout: post
title: "Storyboard Shapes Authoring Tool - Visual Studio 2012"
date: 2012-10-28 14:01:53 +0100
---

![Storyboard Authoring Tool Cover](/assets/images/2012/10/storyboard-authoring-tool-marvel-alm-cover-mohamed-radwan.jpg)

In this post, I will describe everything about the **Storyboard Authoring Tool** or as it is known now, **Storyboard Shapes**. Let’s see the agenda, and you can also watch the following step-by-step video for the whole post: 

{% include embed/youtube.html id='rYO-_RI8RKA' %}

## Agenda

![Storyboard Authoring Tool Questions](/assets/images/2012/10/storyboard-authoring-tool-marvel-alm-questions-mohamed-radwan.jpg)

In this post, I will try to answer the following questions:

- What is the Storyboard Authoring Tool?
- Why use the Storyboard Authoring Tool?
- How to use the Storyboard Authoring Tool?
- A demo on how to create Storyboards with and without the Storyboard Authoring Tool.

![Storyboard Authoring Tool](/assets/images/2012/10/102612_2108_storyboards12.jpg)

Storyboard Shapes Authoring Tool is a command-line tool that was released as a separate exe with the RC version of Visual Studio 2012. It was available at that time in the [Visual Studio Gallery](http://visualstudiogallery.msdn.microsoft.com/ "Visual Studio gallery") and later became part of the [Microsoft Visual Studio Team Foundation Server 2012 Power Tools](http://visualstudiogallery.msdn.microsoft.com/b1ef7eb2-e084-4cb8-9bc7-06c3bad9148f "Microsoft Visual Studio Team Foundation Server 2012 Power Tools") in the RTM of Visual Studio 2012.

![Storyboard Authoring Tool Tasks](/assets/images/2012/10/102612_2108_storyboards22.jpg)

The main tasks of the Storyboard Authoring Tool are to **Build** Storyboard shapes and **Import** Storyboard shapes to the shapes gallery in the add-in.

![Storyboard Authoring Tool GUI](/assets/images/2012/10/102612_2108_storyboards32.jpg)

So, let’s see why we need to use the **Storyboard Authoring Tool** and why we don’t use the Storyboard GUI.

![Storyboard Authoring Tool Bug](/assets/images/2012/10/102612_2108_storyboards41.jpg)

We don’t use the GUI for authoring Storyboard shapes because we can’t edit our shapes gallery if we work on another one. I already opened a bug on [Microsoft Connect](https://connect.microsoft.com/ "Your feedback improving Microsoft products"){target="_blank"} about this issue. **Nathalie**, one of the TFS Product Team, told me that in the meantime, I can use the **Storyboard Authoring Tool** (Storyboard Shapes), and they closed the bug as deferred because they plan to address it in the future, so it’s on their backlog.

![Using Storyboard Authoring Tool](/assets/images/2012/10/102612_2108_storyboards51.jpg)

To use the **Storyboard Authoring Tool** to create shapes, we need to:

- Create a PowerPoint Presentation with specific steps and metadata in the notes.
- Run the **Storyboard Authoring Tool** command line, choose build, and provide the PowerPoint Presentation.
- Produce the .sbsx file that can be imported from the same tool or the GUI if needed.

![Creating Shapes with Storyboard Authoring Tool](/assets/images/2012/10/102612_2108_storyboards6.jpg)

To create shapes using the **Storyboard Authoring Tool**, we will:

- Create a PowerPoint presentation, leave the first slide empty, and add the following metadata in the notes:

    ```
    Reference Name: M.RadwanTools
    Title: M.Radwan Tools
    Type: Category
    Expanded: False
    Version: 1.0
    ```

    ![Metadata Example](/assets/images/2012/10/102612_2108_storyboards7.jpg)

    Remember, the reference should not have any spaces, but it's OK for the title. The type must be **Category** because this is the first slide. The Expanded property is a Boolean that represents whether we want the library to be expanded when we open the storyboard shapes or not.

- Create a slide for each shape and enter the following metadata with different values:

    ```
    Reference Name: BlueText
    Title: Blue Text
    Type: Shape
    ```

    ![Shape Metadata](/assets/images/2012/10/102612_2108_storyboards8.jpg)

    We can also create a slide for each shape preview and set the type as **Shape Thumbnail** so it can be displayed in the shapes preview.

- Run the **Storyboard Authoring Tool** command line and pass it the presentation to produce a .sbsx file.

![Running Storyboard Authoring Tool](/assets/images/2012/10/102612_2108_storyboards9.jpg)
![Produced SBSX File](/assets/images/2012/10/102612_2108_storyboards10.jpg)

- Now, you have the .sbsx file that you can import from the command line or the GUI:

    **Command Line**:

    ![Import via Command Line](/assets/images/2012/10/102612_2108_storyboards111.jpg)

    **GUI**:

    ![Import via GUI](/assets/images/2012/10/102612_2108_storyboards121.jpg)

A look at the metadata:

![Metadata Overview](/assets/images/2012/10/102612_2108_storyboards13.jpg)

Thanks

![Thank You](/assets/images/2012/10/102612_2108_storyboards14.jpg)

![Marvel ALM Microsoft Partner](/assets/images/2012/10/marvel-alm-microsoftt-partner.jpg)
