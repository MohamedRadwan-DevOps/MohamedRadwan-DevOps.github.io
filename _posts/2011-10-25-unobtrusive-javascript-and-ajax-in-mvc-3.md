---
layout: post
title: "Unobtrusive JavaScript and Ajax in MVC 3"
date:   2011-10-25 02:36:26 +0100
---

In the previous release of the ASP.NET MVC which is (MVC 2) I didn\'t
like the Ajax usage, like Ajax action link and Ajax begin form and I
make a rule for the previous project for all my team memebers, that it
is prohibited to use any of them, Why?? Because they generate
inline JavaScript which is the same way as the web form does, this one
of the reason that makes me hit the web form approach. So why I use them
isnted of I can makes a clean JQuery code to
follow JavaScript [Unobtrusive JavaScript](http://en.wikipedia.org/wiki/Unobtrusive_JavaScript "Unobtrusive JavaScript")
which means that we should keep our JavaScript code separated in. js
file, as the CSS it must be separated from the html, the JavaScript also
must be separated from html But in MVC 3 I surprised that all Ajax
action not generate inline scripts and use JQuery and custom html
attributes, we just reference unobtrusive-ajax.js file and of course the
JQuery library, which I can consider it (unobtrusive) as a JQuery
plugin, so now I really consider using Ajax helper method in  my next
proejct

-   See Ajax Begin Form in MVC 2

```xml
<form 
    onsubmit="Sys.Mvc.AsyncForm.handleSubmit(this, new Sys.UI.DomEvent(event), { insertionMode: Sys.Mvc.InsertionMode.replace, updateTargetId: '#myDiv' });" 
    onclick="Sys.Mvc.AsyncForm.handleClick(this, new Sys.UI.DomEvent(event));" 
    method="post" 
    action="/Home/Save">
    
    <input type="text" name="Name">
    <input type="submit" value="Save">
</form>


```

-   See the Ajax Begin from in MVC 3

```xml
<form 
    method="post" 
    id="form0" 
    data-ajax-update="#myDiv" 
    data-ajax-mode="after" 
    data-ajax-method="POST" 
    data-ajax="true" 
    action="/Home/Save">
    
    <input type="text" name="Name">
    <input type="submit" value="Save">
</form>

```

This really show us how Microsoft not only imporove the MVC itself  but
also how they try to follow and lead the web community again as before
:-) 

Thanks Microsoft Keep Improving

