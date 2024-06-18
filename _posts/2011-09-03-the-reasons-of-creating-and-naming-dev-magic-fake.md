---
layout: post
title: "The reasons for creating and naming Dev Magic Fake"
date:   2011-09-03 10:22:58 +0100
---

The main reason for creating this framework is my team members and my managers. Whenever I told any developer on my team to do something as an abstraction and not to worry about the other layers, they couldn't do it. They were always thinking about how this would reflect on the other layers and couldn't grasp the idea of abstraction in development. As a result, the developer would delay their task until the other developer finished the dependent task in the underlying layer. The team couldn't develop by feature because there was a dependency on the underlying layer, which had to be complete before starting the UI.

When I asked our managers about the business requirements, they would provide answers in the form of a database schema. When I told them the schema didn't matter and that I needed to understand the business, they insisted on providing the "how" rather than the "what." Even when I agreed to discuss the "how," they would still not give me a clear answer on the "what." They would often say, "Let's finish the 'how' and we will talk about the 'what' later!"

I always tried to explain to both developers and managers to imagine that I have a magic code that, when instructed to do something, would do it. This code would understand what I needed without having to write the code to do it. But they didn't get my point. So, we had to implement the full feature, the database, and everything. When we finished, the QC would test and start assigning bugs, which we would then fix. Finally, when the customer received the system, they would say, "No, this is not what I need!"

This scenario has repeated throughout my previous 9 years of software development. So, I decided to create a faking framework (Fake) that does what I need without any previous information about the business. I called it "Magic" because it works like magic, and since it's for development (Dev), the name of the framework became:

# Dev Magic Fake

[http://devmagicfake.codeplex.com/](http://devmagicfake.codeplex.com/ "Dev Magic Fake on CodePlex")
