---
title: "Dependency Inversion Principle"
date: 2019-02-22T10:25:49Z
weight: 6
draft: false
---

Dependency Inversion Principle is introduced by Robert C. Martin and his definition is

> A. High-level modules should not depend on low-level modules. Both should depend on abstractions.

> B. Abstractions should not depend upon details. Details should depend upon abstractions.

Let's look at an example of hypothetical mortgage application system. We have higher level `Mortgage` module with `Application` class and `BureauData` module at the next level with `BureauDataProvider` class and at lower level we have `Utility` module with `DataCleaner` class

``` csharp
using BureauData;

namespace Mortgage
{
    public class Application
    {
        public Application(BureauDataProvider dataProvider)
        {

        }
    }
}
```

``` csharp
using Utility;

namespace BureauData
{
    public class BureauDataProvider
    {
        public BureauDataProvider(DataCleaner dataCleaner)
        {

        }
    }
}
```

``` csharp
namespace Utility
{
    public class DataCleaner
    {

    }
}
```

Here the higher level `Application` class directly depends on next level `BureauDataProvider` class and it directly depends on `DataCleaner` class in the lower level. `Application` class indirectly depends on `DataCleaner`. Now, changes to `DataCleaner` or `BureauDataProvider` class may directly affect `Application` class.

This is not a good situation. The higher level module should control the lower level module, not the other way around. Otherwise, changes in lower level classes would force changes on higher level classes and their consumers without adding any value.

In addition to this, when higher level classes directly depends on lower level classes, it is very difficult to reuse higher level classes in different context.

We can use Dependency Inversion Principle to address this issue. We first need to define the abstractions (interfaces) that higher level modules should work with then make the lower level modules implement them.

Here is the revised example

``` csharp
namespace Mortgage
{
    public interface IApplicationBureauDataProvider
    {

    }

    public class Application
    {
        public Application(IApplicationBureauDataProvider dataProvider)
        {

        }
    }
}
```

``` csharp
using Mortgage;

namespace BureauData
{
    public interface IDataCleaner
    {

    }

    public class BureauDataProvider : IApplicationBureauDataProvider
    {
        public BureauDataProvider(IDataCleaner dataCleaner)
        {

        }
    }
}
```

``` csharp
using BureauData;

namespace Utility: IDataCleaner
{
    public class DataCleaner
    {

    }
}
```
