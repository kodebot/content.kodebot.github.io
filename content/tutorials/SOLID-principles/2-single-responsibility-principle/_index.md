---
title: "Single Responsibility Principle"
date: 2019-02-22T10:25:49Z
weight: 2
draft: false
---


Single Responsibility Principle (SRP) is about how we separate or modularise code in object oriented design. This principle says that **a class should have only one reason to change**. 

Robert C. Martin who first introduced this principle says that changes in a class should originate from only single person or a group of people representing a department or business division.

If changes to a class is originating from more than one person/department/division then the class is said to have multiple responsibility and it violates single responsibility principle.
In the context of this principle, we can think of responsibility as "reason to change"

**provide an example that violates SRP**

What we perceive as responsibility or reason to change may be different based on the domain and the problem we are solving.

If we naively over apply this principle to a class, we might end up with what is known as atomised classes where we will have one class with just one method. This is clearly not what we want to achieve with this principle.

To avoid this, Robert C. Martin provided the following definition that complements the previous one


> **Gather together the things that change for the same reasons and separate those things that change for different reason**

If we think about it, this sort of says that we need to increase cohesion and decrease coupling of classes.



Lets look at an example class that does not follow single responsibility principle


example for class that doesn't follow SRP

list the problems it causes

show how it can be refactored to adhere to SRP

References:

https://8thlight.com/blog/uncle-bob/2014/05/08/SingleReponsibilityPrinciple.html
https://hackernoon.com/you-dont-understand-the-single-responsibility-principle-abfdd005b137