---
title: "Mock dependency"
date: 2019-02-22T10:25:49Z
weight: 4
draft: false
---

While fake dependencies are really useful for unit testing, they lack in features like tracking function calls, intercepting arguments, etc.. that makes unit testing easier.
Mock dependency is a dependency which offers all the benefits of fake dependencies and more features to make unit testing easier.

It is not going to be easy to create and maintain mock dependencies; this is why we generally use mocking libraries to create mock dependencies.

{{% img "images/mock-dependency.png" "" 350 %}}

If we take the same passenger discount example that we have seen previously

```
module promotions
    function isPromotionsAvailable():
        .
        .
        .
```

```
module discounts

function isDiscountAvailable(age):
    if promotions.isPromotionAvailable() && age > 60:
        print("discount available")
    else:
        print("discount not available")
```

we create, setup and use mock version of `isPromotionAvailable()` like this in the tests:

```
function test_isDiscountAvailable():
    // arrange
    mockPromotions = mock(promotions) // create mock promotion
    mockPromotions.isPromotionAvailable().return(true) // setup the method to return true
    promotions = mockPromotions // replace promotions with mockPromotions
    age = 65

    // act
    result = discounts.isDiscountAvailable(age)

```

Depending on the language and framework we use, the way we create, setup and use mock dependencies will be different.