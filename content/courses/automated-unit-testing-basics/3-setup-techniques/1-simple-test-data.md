---
title: "Simple test data"
date: 2019-02-22T10:25:49Z
weight: 1
draft: true
---

When we need data, we just create variables with the data and use them in the other places within the unit test.

consider an example of testing a function that adds two numbers

```
function add(a, b):
    return a+b
```

to test this function, we need two input data. 
We can simply create two variables in our test function and use them as arguments for add function. 

```
function test_add():
    // arrange
    a = 10
    b = 15

    // act
    add(a, b)
```