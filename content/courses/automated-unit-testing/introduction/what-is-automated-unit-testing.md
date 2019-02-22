---
title: "What is automated unit testing?"
date: 2019-02-22T10:25:49Z
draft: true
---

Unit testing is targeting small piece of code called unit and test it to verify whether it is working as expected. 

Automated unit testing means, the tests are automated so they will be written once and run as many times as we like.

You can think of unit as a function/subroutine in an application. The tests we write to verify whether the function/subroutine works as expected are called unit tests.
{{% notice info %}}
 *Unit* is loosely defined term and subjective. In most cases you can refer a function/subroutine as unit and depending on the size, complexity and branches available in the function/subroutine, you might write several tests to cover all the scenarios and branches. 
{{% /notice %}}
For example, you might want to write a function in your application to calculate average of two numbers. The tests you write just targeting this function are called unit tests.

{{% notice note %}}
 I will be referring to the **unit** of code we are testing as **System Under Test** or **SUT** going forward.
 {{% /notice %}}