---
title: "System Under Test (SUT)"
date: 2019-02-22T10:25:49Z
weight: 6
draft: true
---

The implementation of System Under Test (SUT) that are the target of our unit test can be one of the following

1. direct implementation
2. indirect implementation
3. combination of the above

## Direct implementation
 If a function or piece of code is direct implementation, then it will take zero or more inputs and provide some results with very little or no dependencies. Functions that implement individual operations of a calculator program like addition, subtraction, etc, a function that creates new student object or a function that validates bank account number are examples of this type of implementation

## Indirect implementation
Normally a function or piece of code falls under this type when it gets something done by communicating with one or more of its dependencies rather than doing something on its own. For example, reading/writing data in database by calling functions in the database driver or validating the account number by calling a function that provides validation

We will also come across many SUT where the implementation is combination of both direct and indirect

We might need to use different techniques for testing SUT depending on their implementation.