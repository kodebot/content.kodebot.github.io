---
title: "Why are we writing unit tests?"
date: 2019-02-22T10:25:49Z
weight: 2
draft: true
---

We can find many reasons for writing unit tests, there are three reasons that stands out in my opinion

* Verify the correctness of the code
* Provide safety-net when we want to change the code (feedback mechanism)
* Serve as a documentation of the code

## Verify the correctness of the code
I don't think any good developer will just write code and say the work is done. They will test it, either via manual steps or by writing automated unit tests, to verify whether the implementation is correct or not.

## Safety-net or feedback mechanism for changes
Once the code is written, we may change it for various reason ranging from changing business requirements to simply to fix a bug in the code. When we want to change code, we need to be very careful to make sure we are not introducing any bugs or unintended side effects. The term used to refer to the bugs or unintended side effects caused by code change is **regression**. Generally, the bigger the program gets the challenging it becomes to keep regression issues under control.  This is where unit tests are really useful. If we have good, solid unit tests covering the current code then we will be able to get immediate feedback on any changes the causes regression issues.

## Documentation of the code
By providing suitable name/description for the tests and keeping it covering all scenarios of the SUT, the tests can be used as a documentation or specification by developers.
