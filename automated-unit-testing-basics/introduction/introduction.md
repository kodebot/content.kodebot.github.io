# Introduction

Welcome to automated unit testing basics course. 

In this chapter lets see what is automated unit testing, why we need them and how it is different from other type of tests. We will also look at different types of code that we generally see in any application. And finally take a brief look at two major approaches when it comes to writing unit tests.

# 1. What is automated unit testing?
Unit testing is targeting small piece of code called unit and test it to verify whether it is working as expected. 

Automated unit testing means, the tests are automated so they will be written once and run as many times as we like.

You can think of unit as a function/subroutine in an application. The tests we write to verify whether the function/subroutine works as expected are called unit tests.

> **Note:** *Unit* is loosely defined term and subjective. In most cases you can refer a function/subroutine as unit and depending on the size, complexity and branches available in the function/subroutine, you might write several tests to cover all the scenarios and branches. 

For example, you might want to write a function in your application to calculate average of two numbers. The tests you write just targeting this function are called unit tests.

# 2. Why are we writing unit tests?
We can find many reasons for writing unit tests, there are two reasons that stands out in my opinion
* Verifying the correctness of the code
* Provides safety-net when we want to change the code (feedback mechanism)

## Verifying the correctness
I don't think any good developer just write code and say the work is done. They will test it somehow to verify whether it works as expected. This testing can be manual or automated. If the develop choose to go down the automated route, then the tests they write will be unit tests.

## Safety-net or feedback mechanism for changes
Once the code is written, we may change it for various reason ranging from changing business requirements to simply a bug in the code. When we want to change code for any reasons, we need to be very careful to make sure we are not introducing any bugs or unintended side effects. This is where unit tests will come to help us. If we have unit tests covering our current code then we will be able to get immediate feedback on any changes we make thus avoiding any unintended side effects or bugs.

# 3. What is good unit test?
Any good unit tests will have the following qualities
* Quick to run
* Repeatable
* Focused
* Isolated
* Self validating

## Quick to run
When running unit test, we don't want to wait long. Because each of the tests we write are focused on one or two lines of the code in our application, we could easily end up with hundreds, if not thousands, of tests even for a small application. Our tests must be extremely fast to get the feedback quickly. So we should try to avoid anything that will slow down our tests.

## Repeatable
We should be able to run our tests repeatedly without any manual interventions. This means anything that our test needs should be setup in the test itself. 

For example, if we need our application to be in a particular state for running a test, then the test itself should bring the application to the desired state as a prerequisite, perform the steps necessary for the test and do any necessary cleanups at the end of the test.

## Focused
We don't want one test trying to testing too many things. Each test should test just one thing. 

For example, if you have a function to calculate the average of two numbers then each test you write should test just one scenario that function presents.

*elaborate with better example*

*add picture*

## Isolated
Any test should not depend on any other test(s). Although it is very common to have one unit of code depends on one or more other units of code, the test you write targetting a particular unit of code should not be affected if any dependent unit of code changes.

*add picture*

## Self validating
Each test you write should give you the feedback at the end on its own. So you don't need to rely on anything other than the test itself for the result of the run.

*elaborate* 

# 4. Tools used for this course
We use C# with .NET Core for this course but the concepts we are going to look at remains same for any similar language/platform.

The tools we are using for this course are
1. Visual Studio 2017 - IDE
2. xUnit.NET - Unit testing framework
3. Moq - Mocking library

You will find equivalent tools for any language/platform you choose.

## Integrated Development Environment (IDE)
This is a tool used for development. IDE usually make developer life easy by offering range of options from intellisense/code completion to building and deploying your code.

## Unit testing framework
A unit testing framework removes the boilerplate needed to write and run automated unit tests. Usually this integrates with your IDE so you can run you tests straight from your IDE.

## Mocking library
Mocking library helps us to build test doubles quickly and easily. They also offer various options to verify the result of our tests. We will go into the details of mocking library in the future chapter.

# 5. What are the other types of automated testing?
While unit tests focus on small unit of code, we have other types of test that generally focus on higher level than unit tests. Two examples of such types of test we have are
* Integration tests
* End to end tests


*elaborate integration test*
*elaborate end to end test*

*provide pyramid example diagram*

# 6. Testing algorithm
* state verification and result verification

# 7. Testing non-algorithm
This type of code can be
* collaborate
* delegate
* orchestrate

This type of code is very common object oriented design.

