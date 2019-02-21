
Welcome to automated unit testing basics course. 

In this chapter lets see what is automated unit testing, why we need them, how it is different from other type of tests. We will also look at different types of code that we generally see in any application. And finally two major approaches when it comes to writing unit tests:   
* Test Oriented approach
* Test Driven approach

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
Any good unit tests will follow the principles below:
* Quick to run
* Repeatable
* Focused
* Isolated
* Self validating

## Quick to run
When running unit test, we don't want to wait long. Because each of the tests we write are focused on one or two lines of the code in our application, we could easily end up with hundreds of tests even for a small application. So our tests must be extremely fast to get the feedback quickly. So we should try to avoid anything that will slow down our tests.

## Repeatable
We should be able to run our tests repeatedly without any manual interventions. This means anything that our test needs should be setup in the test itself. 

For example, if we need if we need our application to be in a particular state for running a test, then the test itself should move the application to the desired state as a prerequisite and do any necessary cleanups at the end of the test.

## Focused
Each test should try to test just one thing. *elaborate* 

## Isolated
Test should not depend on other tests. Should not depend on environment data. Should not depend on the correctness of other unit of code that this unit interacts with.

## Self validating
*elaborate* 