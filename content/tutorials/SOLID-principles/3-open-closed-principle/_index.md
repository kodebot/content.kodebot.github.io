---
title: "Open-Closed Principle"
date: 2019-02-22T10:25:49Z
weight: 3
draft: false
---

Open-Closed Principle says software must be open for extension but closed for modification. When you first hear this, it might sound like oxymoron but it is not when you understand this properly. 

This principle was first introduced by Bertrand Meyer and his definition of this principle is:

> Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification.

Later, Robert C. Martin provided the following improved definition which is suitable for modern software development

> You should be able to extend the behaviour of a system without having to modify that system

Lets try to understand this in detail. How can a software be open for extension and closed for modification? After all, if you want to add new functionality or change existing functionality, you need to change the code. And yes, this is correct. So what this principle is actually talking about?

The principle says that we need to identify changes that are frequent and keep the parts affected by that change open for extension and keep the parts that are not affected close for modification.

Lets look at an example to make this clear. We have a `TaxCalculator` here that calculates tax for given income. 

``` csharp
public class TaxCalculator
{
    public decimal Calculate(decimal income){
        return income * 0.2m;
    }
}

```
We know that tax rates differ by country in addition to several other factors. For simplicity, we will assume that each county has fixed tax rate and not affected by anything else.

We can say the code in the example above confirms to open-closed principle as long as the calculate method doesn't need to be changed. This will be the case when the `TaxCalculator` class supports only one country assuming tax rates for the country is not changed frequently.

On the other hand, if we want to support tax calculation for other countries and we frequently add support for new country then each time we add support for new country, we need to "modify" `Calculate()` as in the example below

``` csharp
public class TaxCalculator
{
    private readonly Country _country;
    
    public TaxCalculator(Country country)
    {
        _country = country;
    }

    public decimal Calculate(decimal income)
    {
        switch(_country)
        {
            case Country.UK:
                return income * 0.2m;
            case Country.USA:
                return income * 0.25m
        }
    }
}

```

This is definitely not confirming to open-closed principle.

Now we know that the way we calculate tax is different for each country and we are going to add support for more countries frequently. So, we need to make the code in `Calculate()` method open for extension but keep the `TaxCalculator` class and its contract closed for modification. This is because, we don't want to affect the consumers of `TaxCalculator` class affected whenever a new country is added.


One of the way we can achieve this is using abstraction. We can 


Add new features without changing old code

plugin model is best example

code injections - functions, interface/abstract class or partial abstract classes

You need to find out what you want to close and what you want to open for extension and design the system accordingly

educated guess


strategy pattern

template method pattern (partial abstract class)

``` csharp

// tax calculator example

```

provide an example of change to the closed module - there may be scenarios where you might need to change the closed module

You need to guess the part you want to closed and the part you want to open. confirming to this principle is expensive in terms of initial development cost so you need to find right balance

we need to find out the parts that will change frequently early as changes in the later stages are generally more difficult

Robert C. Martin says "Resisting premature abstraction is as important as abstraction itself"


### References
https://hackernoon.com/why-the-open-closed-principle-is-the-one-you-need-to-know-but-dont-176f7e4416d
https://blog.cleancoder.com/uncle-bob/2014/05/12/TheOpenClosedPrinciple.html
