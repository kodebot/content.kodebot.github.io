---
title: "State verification"
date: 2019-02-22T10:25:49Z
weight: 2
draft: true
---

State verification is similar to result verification but rather than checking the result of the function, we check the state of an object or something similar. 

consider an example of testing a function that closes database connection

```
module databaseManager

isOpen

function close():
    isOpen = false
```

When we call this function, it is not going to return anything, instead it is going to change the state of `isOpen` field

So we need to verify the state of `isOpen` field to ensure the correctness of `close` function

```
function test_close():
    // arrange
    databaseManager.isOpen = true

    // act
    databaseManager.close()

    // assert
    areEqual(false,  databaseManager.isOpen) // false is expected

```