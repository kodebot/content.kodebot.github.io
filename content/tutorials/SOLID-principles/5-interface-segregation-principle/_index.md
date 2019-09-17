---
title: "Interface Segregation Principle"
date: 2019-02-22T10:25:49Z
weight: 5
draft: false
---
Interface Segregation Principle was introduced by Robert C. Martin. His definition of this principle is

> Clients should not be forced to depend on methods it does not use

There may be scenarios where we may have a class that has members used by two or more clients. When changing any of the members used by one client, all the clients of the class, even the ones that are not using the changing members, are affected. 

Robert C. Martin describes these type of classes as "Interface Pollution". In this context, "interface" refers to the public members (fields, properties and methods) of the class.

As per Interface Segregation Principle, we should have one interface per client with just enough members needed for that client.

This is better understood with an example. Let's say we have `Order` class

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

This class clearly contains methods that are used by two different clients - Customer user interface and Seller user interface.

While it is best to avoid this type of classes, it is not always possible. 

The problems we face with this type of classes may be debatable, however it is definitely a good idea to have client specific interface that exposes just enough members for each client. 

The key benefit of having client specific interface is that it allows clients to see only what it needs to see so the collaboration between the class and the client is clear. Also, it completely eliminates the chance of misuse, i.e. client user interface calling `Dispatch()` method.
 
Martin Fowler calls this type of interface as [role interface](https://www.martinfowler.com/bliki/RoleInterface.html)

In our example, we will create the following two interfaces, one for each client, as per Interface Segregation Principle

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

The `Order` class still contains all the methods but it now implements both `ICustomerOrder` and `ISellerOrder` interfaces

``` csharp
public class Order : ICustomerOrder, ISellerOrder
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

The customer user interface can use the `ICustomerOrder` abstraction rather than `Order` class directly. This way, customer user interface won't see any methods that it should not use. 

Likewise, seller user interface can use `ISellerOrder` and it won't see any methods that it should not use.


### References

1. https://drive.google.com/file/d/0BwhCYaYDn8EgOTViYjJhYzMtMzYxMC00MzFjLWJjMzYtOGJiMDc5N2JkYmJi/view

2. https://en.wikipedia.org/wiki/Interface_segregation_principle

