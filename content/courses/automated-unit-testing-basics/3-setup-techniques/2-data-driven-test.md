---
title: "Data driven test"
date: 2019-02-22T10:25:49Z
weight: 2
draft: true
---

When we want to test a method, we usually want to test with different set of data. It is not ideal to create one test function for one set of input data.
This is where data driven tests are helpful.

consider the same example function that adds two numbers

```
function add(a, b):
    return a+b
```

to be thorough we need to test this function with few different set of data includes negative number, positive numbers and zeros. 

Although, it will be descriptive to easy to follow when we have one test test function per input data, it requires more development and maintenance work. 

Better solution is to create one test function that we can run with different set of data. This is what we call data driven tests.

An example of data driven test would look like this

```
type DataTest:
    input1
    input2
    result

function test_add():
    // arrange
    tests = [
        [input1: 1, input2: 2, result: 3],
        [input1: -1, input2: -1, result: 0],
        [input1: 1, input2: -2, result: -1],
    ]

    // act
    loop test of tests:
        add(test.input1, test.input2)
```

The actual implementation of data driven language will different based on the language and the framework used.