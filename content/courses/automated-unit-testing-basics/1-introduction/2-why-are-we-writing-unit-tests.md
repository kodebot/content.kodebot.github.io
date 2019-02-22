---
title: "Why are we writing unit tests?"
date: 2019-02-22T10:25:49Z
weight: 2
draft: true
---

We can find many reasons for writing unit tests, there are three reasons that stands out in my opinion

* Verifying the correctness of the code
* Provides safety-net when we want to change the code (feedback mechanism)
* Serves as a documentation of the code

## Verifying the correctness
I don't think any good developer just write code and say the work is done. They will test it somehow to verify whether it works as expected. This testing can be manual or automated. If the develop choose to go down the automated route, then the tests they write will be unit tests.

## Safety-net or feedback mechanism for changes
Once the code is written, we may change it for various reason ranging from changing business requirements to simply a bug in the code. When we want to change code for any reasons, we need to be very careful to make sure we are not introducing any bugs or unintended side effects. This is where unit tests will come to help us. If we have unit tests covering our current code then we will be able to get immediate feedback on any changes we make thus avoiding any unintended side effects or bugs.

## Documentation of the code
By providing suitable name/description for the tests and keeping it covering all scenarios of the SUT , it can be used as a documentation or specification.
