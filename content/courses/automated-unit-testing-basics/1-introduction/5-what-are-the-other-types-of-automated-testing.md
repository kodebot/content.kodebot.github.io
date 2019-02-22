---
title: "What are the other type of automated testing"
date: 2019-02-22T10:25:49Z
weight: 5
draft: true
---

While unit tests focus on small unit of code, we have other types of test that generally focus on higher level than unit tests. Two examples of such types of test we have are

* Integration tests
* End to end tests

When SUT has any dependencies then as a general rule, you will create alternative version of that dependency called test double, either manually or using mocking library, and use the test double in your tests by substituting it for the original dependencies. You will do this to keep your unit tests focused and not influenced by the behaviors of the dependencies of the SUT. While this is correct approach for unit tests, it doesn't provide coverage for SUT with real dependencies. Integration and End to end tests falls under this category where SUT will be tested with real dependencies.

Integration tests aim testing SUT with one or more dependencies and may use test doubles when required. On the other hand End to end test try to test the application just like how end user will use it. End to end tests generally uses publicly accessible parts like UI or API interface for testing. While it is not common,  end to end tests can use test doubles if required but it should be kept to minimum.

When writing tests for any application, we should use Integration and End to end tests along with Unit tests. 

People use the following pyramid diagram to show the distribution of these three types of tests.

*provide pyramid example diagram*

As you can see, Unit tests should be the majority. We should use Integration and End to end tests as and when they are required but they are small in number compared to Unit tests.
