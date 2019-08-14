---
title: "Result verification"
date: 2019-02-22T10:25:49Z
weight: 1
draft: false
---

We use result verification technique when the test receives the result by running SUT. 

Consider an example of testing a function that adds two numbers and returns the result

```
function add(a, b):
    return a+b
```

we verify the correctness of this function by simply checking the result returned by add function

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