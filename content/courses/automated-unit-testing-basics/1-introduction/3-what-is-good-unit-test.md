---
title: "What is good unit test?"
date: 2019-02-22T10:25:49Z
weight: 3
draft: true
---

When writing tests for any block of code, it must be comprehensive and cover all the scenarios. If you write tests for most obvious scenarios and don't cover the less common scenarios then you are don't know how it is going to behave on those untested scenarios.

Each test you write should have the following qualities

* Quick to run
* Repeatable
* Focused
* Isolated
* Self validating

## Quick to run
When running unit test, we don't want to wait long. Because each of the tests we write are focused only on few lines of the code in our application, we could easily end up with hundreds, if not thousands, of tests even for a small application. Our tests must be extremely fast to get the feedback quickly. So we should try to avoid anything that will slow down our tests.

## Repeatable
We should be able to run our tests repeatedly without any manual interventions. This means anything that our test needs should be setup in the test itself. 

For example, if we need our application to be in a particular state for running a test, then the test itself should bring the application to the desired state as a prerequisite, perform the steps necessary for the test and do any necessary cleanups at the end of the test.

## Focused
We don't want one test trying to testing too many things. Each test should test just one thing. 

For example, if you have a function to validate bank account number and valid account number is eight digit numeric value then you should try to create one test for each validation criteria. That is one test for each of the scenarios listed below

* verify account number is not null or empty
* verify account number is exactly 8 characters
* verify account number is only contains digits

*TODO:add picture*

## Isolated
Any test should not depend on any other test(s). Although it is very common to have one function or object depends on one or more other functions or objects, the test you write targeting a particular block of code should not be affected if the behavior of any of its dependent functions or objects changes.

*add picture*

## Self validating
Each test you write should give you the feedback at the end on its own. You should not rely on anything other than the test itself for the result of the run.
