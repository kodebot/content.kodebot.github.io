---
title: "Structure"
date: 2019-02-22T10:25:49Z
weight: 1
draft: true
---

Any unit test will have two or more of the following steps
1. Setup
2. Run SUT
3. Verification
4. Cleanup

## Setup
One of the first step in writing unit test is **Setup**. In this step, we prepare test data, dependencies and the context for the test.

For example, we will replace any real dependencies with fake ones and define set good test data as part of this step.

However, this step is not necessary for all the tests.

This step is commonly referred to as **Arrange** or **Fixture setup**

## Run SUT
This is the step that runs the SUT with test data and fake dependencies. This is a mandatory step for any unit test.

This step is commonly referred to as **Act** or **Exercise sut**

## Verification
This step verifies the result of running SUT under test condition. This is a mandatory step.

This step is commonly referred to as **Assert** or **Verify Outcome**

## Cleanup
This is optional step and needed only when any clean up is required after the test run. This step is commonly referred to as **Fixture teardown**

# AAA
One of the popular acronym for testing steps or phases is AAA and it refers to Arrange, Act and Assert. Since Cleanup is not very common step, it is omitted.