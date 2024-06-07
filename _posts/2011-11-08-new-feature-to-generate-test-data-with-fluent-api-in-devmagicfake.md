---
layout: post
title: "New Feature to generate test data with fluent API in DevMagicFake"
date:   2011-11-08 00:18:28 +0100
---

Hello, I received very good suggestions and feedback from [Maatren  Balliauw](http://blog.maartenballiauw.be/ "Maartenballiaw"), really thanks Maarten for your valuable opinions and ideas  :-) the most
important suggestion was about making a fluent interface for
my framework (DevMagicFake), of course there are data generation but
with file configuration only, I planned to support better way but really
Maatern give me very good opinions,  And now I complete this feature and
here how it will work When we work we need test data for testing our
application, we need generator for our classes so we can perform the
desired business scenarios, now we can use DevMagicFake for data
generation in our domain model using fluent API instead of file
configuration. [Note: this feature not released yet, so if anyone need
to use it, he will need to download the latest reversion of
the project from CodePlex and just make a local build on his
machine.]{style="color: #ff0000;"} So if we write the following code

[![](/assets/images/2011/11/FluentCode.png)](/assets/images/2011/11/FluentCode.png)

So this will generate data as the following:

[![FluentAPIResult](/assets/images/2011/11/FluentAPIResult.png)](/assets/images/2011/11/FluentAPIResult.png)

The rules can be set using the following methods:

[![FluentAPI](/assets/images/2011/11/FluentAPI.png)](/assets/images/2011/11/FluentAPI.png)

Now there are 3 methods for putting rules for your data generation

-   RuleUsesClassProperty( )
-   RuleUsesDataType( )
-   RuleUsesPropertyOnly( )

Each method can use one of the 4 types of generation of the following

-   GeneratFromList()
-   GenerateFromRange( )
-   GenerateFromValue( )
-   GenerateFromRandom( )

Finally you can controller the null percentage if needed

-   NullPercentage( )

And remember the data generation is a secondary goal of DevMagicFake ,
the main goal is to provide a way of real repository for your business
classes in memory with all the methods that you may need to
stop writing any faking code and be productive and working real TDD
(Test Driven Development ) and (Test Driven Design) I hope to get more
feedback for improvement and new feature that will really help. 

Thanks

