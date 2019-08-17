---
title: "What is good unit test?"
date: 2019-02-22T10:25:49Z
weight: 3
draft: false
---

When writing tests for any block of code, it must be comprehensive and cover all the scenarios. If we write tests for most obvious scenarios and don't cover the less common scenarios then we don't know how it is going to behave on those untested scenarios.

Each test we write should have the following qualities

* Quick to run
* Repeatable
* Focused
* Isolated
* Self validating

## Quick to run
When running unit test, we don't want to wait long. Because each of the tests we write target only few lines of the code, we could easily end up with hundreds, if not thousands, of tests even for a small program/application. Our tests must be extremely fast to get the feedback quickly. So we should try to avoid anything that will slow down our tests. When this is not possible, we should at least be able to keep the slow running tests separate and run them independently without affecting fast running tests.

## Repeatable
We should be able to run our tests repeatedly without any manual interventions. This means anything that our test needs should be done in the test itself. 

For example, if we need our application to be in a particular state for running a test, then the test itself should bring the application to the desired state as a prerequisite, perform the steps necessary for the test and do any necessary cleanups at the end of the test.

## Focused
We don't want one test trying to verify too many things. Each test should verify just one thing. 

For example, if we have a function to validate bank account number then we should try to create one test for each validation rule. That is, one test for each of the rules listed below

* verify account number is not null or empty
* verify account number is exactly 8 characters
* verify account number is only contains digits

## Isolated
Any test should not depend on any other test(s). Although it is very common for a function or object to depend on other functions or objects, the test we write targeting a particular block of code should not be affected if the behavior of any of its dependent function or object changes.

## Self validating
Each test we write should give us the feedback at the end on its own. We should not rely on anything other than the test itself for the result.
