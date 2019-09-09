---
title: "Other types of automated testing"
date: 2019-02-22T10:25:49Z
weight: 4
draft: false
---

While unit test targets small piece of code, we have other types of test that generally focus at higher level than unit tests. Two examples of such types of test we have are

* Integration tests
* End to end tests

Generally, unit tests focus on small piece of code without considering the behavior of dependencies they have (usually with the help of fake dependencies). This means we will be able to verify whether the target code works on it own or not, but we will not know whether it is going to work correctly as a part of bigger program. While this is the correct approach for unit tests, it doesn't cover verifying the behavior with real dependencies. Integration and End to end tests falls under this category where SUT will be tested with real dependencies.

Integration tests aim testing SUT with one or more real dependencies and may use some fake dependencies if required. On the other hand End to end test try to test the application just like how end user will use it. End to end tests generally use publicly accessible parts like UI or API for testing. While it is not common, end to end tests can use fake dependencies if required but it should be kept to minimum.

When writing tests for any application, we should use Integration and End to end tests along with Unit tests. 

People use the following pyramid diagram to show the distribution of these three types of tests that we should have for any program/application.

{{% img "images/testing pyramid.png" "" 250 %}}

As we can see, Unit tests should be the majority. We should use Integration and End to end tests as and when they are required but they are small in number compared to Unit tests.
