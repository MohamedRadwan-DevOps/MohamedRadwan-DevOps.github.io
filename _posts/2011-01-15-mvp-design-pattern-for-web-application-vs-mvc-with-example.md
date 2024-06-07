---
layout: post
title: "MVP design pattern for Web application vs. MVC, with Example"
date:   2011-01-15 03:51:08 +0100
---

I start reading about MVP design pattern in web application and I found
it very useful, but I get out of one main important concept, the MVP
pattern is very good in web application if we working with ASP.NET Web
Forms because it will make the model testable but if we working with MVC
it\'s already a testable and more and more it can be TDD (Test driven
Development) model, of course this not the only reason for MVP or MVC
they also enhance the maintainability of the web application and there
are many other reasons for using them. I read many articles about MVP
but most of my writing come from 
[dot net miscellany](http://blogs.msdn.com/b/jowardel/archive/2008/09/09/using-the-model-view-presenter-mvp-design-pattern-to-enable-presentational-interoperability-and-increased-testability.aspx?ocid=soc-n-eg-elite--MRadwan "Source")

I create a Web form application that has MVP pattern that can download
from the following link download

[![Download](assets/img/2011/01/download.jpg)](assets/img/2017/08/MVP.zip)

So let\'s start what is the MVP pattern?

[![MVP](assets/img/2011/01/MVP-1-1024x673.png)](assets/img/2011/01/MVP-1.png)

Model View Presenter (MVP) is a software design pattern which
essentially isolates the user interface from the business logic through
the presenter. MVP is derived from the Model View Controller (MVC)
pattern, by Martin Fowler. The principal behind the MVP pattern is that
an implementing application should be split into three core components;
Model, View and Presenter: The main concept of the MVP is that the UI is
separated from the business logic and this could have many advantages as
we will see

-   The Model component encapsulates all the Data in the application.
    This may be a database transaction or a call to a web service, or
    any persistence or even volatile data

<!-- -->

-   The View component is the Presentation layer (User Interface); this
    may be a standard Win Forms client, an ASP.NET Web Form or Web part
    or Mobile client. In the MVP pattern, it will handle the rendering
    and accepting user input only.

<!-- -->

-   The Presenter is controlling of the application\'s actions. For
    example a sample operation would involve; taking user input from the
    View, invoking operations on the Model and if needed, setting data
    in the View to indicate the operations result and so on.

The advantages of MVP pattern are:

-   Isolation of User Interface from Business logic
-   The ability to change the UI from Web to Window or Mobile is very
    easy
-   Ability to test all code in the solution for all projects (excluding
    visual presentation and interaction)

We can see here that we can separate the physical class of the MVP in
separate assemblies like the following architecture and layer diagram:

[![MVP Architecture](assets/img/2011/01/MVP-Architecture.png)](assets/img/2011/01/MVP-Architecture.png)

You can download the project as I mention before from the above download
link For more information you can read the following post:

[MSDN](http://msdn.microsoft.com/en-us/magazine/cc188690.aspx "MSDN")

Thanks
