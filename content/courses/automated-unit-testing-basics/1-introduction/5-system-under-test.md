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
 If a function or piece of code is direct implementation, then it will take zero or more inputs and provide some results or cause state change with very little or no dependencies. 
 
 Examples of direct implementation
 
 * Functions that implement individual operations of a calculator program like addition, subtraction, etc... 
 * Function that creates new student object 
 * Function that validates bank account number

## Indirect implementation
Normally a function or piece of code falls under this type when it gets something done via one or more of its dependencies rather than doing it on its own. 

Examples of indirect implementation

* Reading/writing data in database by calling functions in the database driver 
* Validating the account number by calling a function that provides validation

## Direct and indirect
We will also come across many SUT where the implementation is combination of both direct and indirect

It is good to be aware of these types because we might need to use different techniques for testing depending on their implementation type.