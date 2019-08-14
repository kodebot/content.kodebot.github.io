---
title: "What is automated unit testing?"
date: 2019-02-22T10:25:49Z
weight: 1
draft: true
---

Let's first understand what we call as **Unit**. The term unit is very subjective, so it means different things to different people. In the context of testing, I like to think of unit as one or more lines of code that does something small but tangible to move towards achieving the end goal of the program. 

What do I mean by this? Well, lets look at an example of a very simple calculator program. In order to build a calculator, we need to build individual operations that are supported by the calculator. Each simple operations like addition, subtraction, multiplication and division are implemented using few lines of code and these operations are units as these are small but tangible steps needed to build a calculator.

However, we cannot say all the operations supported by a calculator are made up of single unit. There are some operations like average, percentage, etc are not simple ones and they are implemented using **group** of units. For example, average is implemented using addition and division.

{{% notice info %}}
 *Unit* is loosely defined term and subjective. In most cases you can refer a small function/subroutine as unit but it is not always true. There may be functions/subroutines that are made up of group of units.
 {{% /notice %}}

So, Unit testing is taking a small piece of code that is written to do something small but tangible and test it to verify whether it is working as expected or not. 

Automated unit testing means, the unit testing process is automated by writing code, so the tests are written once and run as many times as we like without any manual overhead. 

For example, the tests you need for the individual units of a calculator program are called unit tests. If those tests are automated with code then you can refer to them as automated unit tests.

{{% notice note %}}
 I will be referring to the **unit** of code we are testing as **System Under Test** or **SUT** and **automated unit test** as simply **unit test** going forward.
 {{% /notice %}}