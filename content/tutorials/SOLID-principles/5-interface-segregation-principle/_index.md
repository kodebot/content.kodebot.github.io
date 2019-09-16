---
title: "Interface Segregation Principle"
date: 2019-02-22T10:25:49Z
weight: 5
draft: false
---
Interface Segregation Principle was introduced by Robert C. Martin. His definition of this principle is

> Clients should not be forced to depend on methods it does not use

There may be scenarios where we may have a class that provides the functionalities used by two or more clients. When changing something on that class used by a particular client, all the clients of the class, even the ones that are not using the changing functionality, are affected.

This is better understood with an example. Let's say we have a class called `Subscription` with `Renew()` method

``` csharp
public class Subscription
{
    pubic void Renew()
    {
        // renew current subscription
    }
}
```


explain what is Interface Segregation Principle

example for class that doesn't follow Interface Segregation Principle

list the problems it causes

show how it can be refactored to adhere to Interface Segregation Principle

### References

https://drive.google.com/file/d/0BwhCYaYDn8EgOTViYjJhYzMtMzYxMC00MzFjLWJjMzYtOGJiMDc5N2JkYmJi/view

https://en.wikipedia.org/wiki/Interface_segregation_principle

