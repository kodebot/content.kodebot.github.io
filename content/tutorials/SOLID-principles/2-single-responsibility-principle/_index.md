---
title: "Single Responsibility Principle"
date: 2019-02-22T10:25:49Z
weight: 2
draft: false
---


Single Responsibility Principle (SRP) is about how we separate or modularise code in object oriented design. This principle says that **a class should have only one reason to change**. 

If we naively apply this principle, we will end up with several classes where each class contains just one method that just does one small thing. This leads to unnecessary complexity. This is clearly not what we want to achieve with this principle.

Robert C. Martin who introduced this principle clarified that this principle is "about people" and also provided the following complementing definition.

> **Gather together the things that change for the same reasons and separate those things that change for different reason**

So, changes to a class should originate from only single person or a group of people representing a department or business division or similar.

If changes to a class is originating from more than one person/department/division then the class is said to have multiple responsibilities and it violates single responsibility principle.

The complementing definition sort of says that we need to increase cohesion and decrease coupling of classes. So this will help us avoid atomised classes.

{{%notice info %}}
In the context of this principle, we can think of responsibility as "reason to change". What we perceive as responsibility or reason to change may be different based on the domain and the problem we are solving.
{{%/notice%}}

** example for class that violates SRP **

** refactor the class to adhere to SRP**

References:

https://8thlight.com/blog/uncle-bob/2014/05/08/SingleReponsibilityPrinciple.html
https://hackernoon.com/you-dont-understand-the-single-responsibility-principle-abfdd005b137