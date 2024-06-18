---
layout: post
title: "How to limit the Pex to not explorer every block in your application"
date:   2011-07-20 20:30:33 +0100
---

MS Pex one of the greatest tool I found for automation of
the generation of the unit testing, but when you Pex your application
you don\'t want Pex exploration to run for every method called for the
desired method, so you can use some attributes to define this option
PexInstrumentAssemblyAttribute Specifies to instrument an assembly
PexInstrumentTypeAttribute Specifies to instrument a type
PexAssemblyUnderTestAttribute Binds a test project to a project

```csharp
[assembly:PexAssemblyUnderTest("MyAssembly")]
[assembly:PexInstrumentAssembly("Lib")]
[assembly:PexInstrumentType(typeof(MyClass))]

```

