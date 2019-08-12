---
title: "What is automated unit testing?"
date: 2019-02-22T10:25:49Z
weight: 1
draft: true
---

Lets first understand what we call as **Unit**. The term unit is very subjective, so, it means different things to different people. In the context of testing, I like to think of unit as one or more lines of code that does something small but tangible to acheive the end goal of the program. 

What do I mean by this? Well, lets look at an example of a very simple calculator program. In order to build a calculator, we need to build individual operations that are supported by the calculator. Each simple operations like addition, subtraction, mutiplication and division are implemented using few lines of code and they are examples of units. 

However, we cannot say all the operations supported by a calcultor are units. There are some operations like average, percentage, etc are not simple ones and they are implemented using **group** of units. For example, average is implemented using addition and division.

So, Unit testing is taking a small piece of code that is written to do something small but tangible and test it to verify whether it is working as expected or not. 

Automated unit testing means, the tests are automated by writing code, so,  they will be written once and run as many times as we like. 

{{% notice info %}}
 *Unit* is loosely defined term and subjective. In most cases you can refer a function/subroutine as unit and depending on the size, complexity and branches available in the function/subroutine, you might write several tests to cover all the scenarios and branches. 
{{% /notice %}}

For example, you might want to write a function in your application to calculate average of two numbers. The tests you write just targeting this function are called unit tests.

{{% notice note %}}
 I will be referring to the **unit** of code we are testing as **System Under Test** or **SUT** going forward.
 {{% /notice %}}