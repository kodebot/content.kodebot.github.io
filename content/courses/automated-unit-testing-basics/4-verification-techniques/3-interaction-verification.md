---
title: "Interaction verification"
date: 2019-02-22T10:25:49Z
weight: 3
draft: true
---

Interaction verification is completely different from result and state verification. With this technique, we will be checking whether an interaction under a specific condition has happened or not.

consider the example below, the databaseManager module offers a method to close database but it neither returns any result nor changes the state. All this method does is that it calls a method in database module.

```
module databaseManager

function close():
    database.close()
```

So, the only thing we can do to verify the correctness of this function is to check whether it calls `close()` function in database module

```
function test_close():
    // arrange
    mockDatabase = mock(database)
    database = mockDatabase

    // act
    databaseManager.close()

    // assert
    mockDatabase.close().calledOnce()   

```