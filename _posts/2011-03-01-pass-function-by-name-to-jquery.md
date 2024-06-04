---
layout: post
title:  "How to pass function by name variable not by body to JQuery?"
date:   2011-05-01 07:40:05 +0100
---

It is a very small tip but the final comments are very important and it just here for fast remember, the story begin when I start re-factoring my team JQuery code, I found that there are many functions passed by body and inside these function another many functions also passed by body and most of these functions repeated with no need and the code
become terrible and can\'t maintained specially for someone like me that didn\'t write JQuery everyday :-) So all you need to do just declare a function and pass it like the following: 

```javascript

<script language="javascript" type="text/javascript">
    var func1 = function () {
        alert("Finished");
    };

    var func2 = function () {
        $("#div2").fadeOut(5000, func1);
    };

    $("#div1").click(func2);
</script>

```

-   My mistake was I was pass the function with the parentheses, so I
    only need to write the function name and if I write the parentheses
    it will give me errors
-   If  I create a function that take parameters I can\'t pass
    parameters in a callback
-   Remember who call the callback, if the JQuery do?  it will pass the
    parameters that needed if the callback signature require parameters
    like the function exist in the Ajax request callback which has
    parameter data that response from the request
-   The function must be declare before the usage of  it in the code so
    consider the arrange of the code
-   Remember you can call a function and pass a parameters normally
    inside any function but the key here that you can\'t pass parameter
    when you register or passing the function to JQuery code
-   ddd

```javascript

<script language="javascript" type="text/javascript">
    var text = "Hello";
</script>

<script language="javascript" type="text/javascript">
    var func1 = function () {
        alert(text + " Seif and Lara");
    };

    var func2 = function () {
        $("#div2").fadeOut(5000, func1);
    };

    var s = "#div" + 1;
    $(s).click(func2);
</script>

```

