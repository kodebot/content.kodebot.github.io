---
title: "Interface Segregation Principle"
date: 2019-02-22T10:25:49Z
weight: 5
draft: false
---
Interface Segregation Principle was introduced by Robert C. Martin. His definition of this principle is

> Clients should not be forced to depend on methods it does not use

There may be scenarios where we may have a class that provides the functionalities used by two or more clients. When changing something on that class used by a particular client, all the clients of the class, even the ones that are not using the changing functionality, are affected.

This is better understood with an example. Let's say we have `Order`

``` csharp
public class Order
{
    pubic void Create()
    {
        // create order for product(s)
    }

    public void Update()
    {
        // update order
    }

    public void Cancel()
    {
        // cancel order
    }

    public void Return()
    {
        // return ordered product(s)
    }

    public void Track()
    {
        // track order 
    }

    public void Process()
    {
        // process order
    }

    public void Dispatch()
    {
        // dispatch order
    }

    public void ProcessCancellation()
    {
        // process cancellation
    }

    public void ProcessReturn()
    {
        // process return
    }
}
```

This class clearly contains methods that are used by two different clients - Customer UI and Seller UI.

While it is best to avoid this type of classes, it is not always possible. Robert C. Martin describes these type of classes as "Interface Pollution". In this context, "interface" refers to the public members (fields, properties and methods) of the class.

While the problems we face with this type of classes is debatable, it is definitely good idea to have client specific interface that exposes just enough member for the client it is used by. Martin Fowler calls this type of interface as [role interface](https://www.martinfowler.com/bliki/RoleInterface.html)

In our example, we will have the following two interfaces

``` csharp
public interface ICustomerOrder
{
    void Create();
    void Update();
    void Cancel();
    void Return();
    void Track();
}
```

``` csharp
public interface ISellerOrder
{
    void Process();
    void Dispatch();
    void ProcessCancellation();
    void ProcessReturn();
}
```

The `Order` class will implement both `ICustomerOrder` and `ISellerOrder` interfaces.

Now, the customer user interface can use the `ICustomerOrder` abstraction rather than `Order` class directly. Likewise, seller user interface can use `ISellerOrder`

### References

1. https://drive.google.com/file/d/0BwhCYaYDn8EgOTViYjJhYzMtMzYxMC00MzFjLWJjMzYtOGJiMDc5N2JkYmJi/view

2. https://en.wikipedia.org/wiki/Interface_segregation_principle

