---
title: "Test oriented"
date: 2019-02-22T10:25:49Z
weight: 2
draft: true
---

Any unit test will have two or more of the following steps

1. Setup
2. Run SUT
3. Verification
4. Cleanup

## Setup
One of the first step in writing unit test is **Setup**. In this step, we prepare test data, dependencies and/or the context for the test.

For example, we will replace any real dependencies with fake ones and define set of good test data as part of this step.

However, this step is not necessary for all the tests.

This step is commonly referred to as **Arrange** or **Fixture setup**

## Run SUT
This is the step that runs the SUT with test data and/or fake dependencies. This is a mandatory step for any unit test.

This step is commonly referred to as **Act** or **Exercise sut**

## Verification
This step verifies the result of running SUT under test condition. This is a mandatory step.

This step is commonly referred to as **Assert** or **Verify Outcome**

## Cleanup
This is optional step and needed only when any clean up is required after the test run. This step is commonly referred to as **Fixture teardown**

# AAA
One of the popular acronym for testing steps or phases is AAA, and it refers to Arrange, Act and Assert. Because cleanup is not a common step, it is omitted.

Here is an example of AAA pattern test:

```
function test_add():
    // arrange
    a = 10
    b = 15

    // act
    result = add(a, b)

    // assert
    areEqual(25, result) // 25 is expected

```