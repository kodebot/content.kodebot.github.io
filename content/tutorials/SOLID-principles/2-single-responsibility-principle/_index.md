---
title: "Single Responsibility Principle"
date: 2019-02-22T10:25:49Z
weight: 2
draft: false
---

Single Responsibility Principle (SRP) states that every module, class and function should have only one responsibility. Another way to look at it is that every module, class and function should have only one reason to change.

?? should the definition be extended to module and functions ??

What we perceive as responsibility or reason to change may be different based on the domain and the problem we are solving.

Robert C. Martin recently clarified that this principle is about people. (provide link)

Sort of saying increase cohesion and decrease coupling.

Lets look at an example class that does not follow single responsibility principle


https://8thlight.com/blog/uncle-bob/2014/05/08/SingleReponsibilityPrinciple.html

>> Gather together the things that change for the same reasons and separate those things that change for different reason

example for class that doesn't follow SRP

list the problems it causes

show how it can be refactored to adhere to SRP