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

Now if we look at the `Application` class in `Mortgage` module, it depends on `IApplicationBureauDataProvider` interface which is defined in `Mortgage` module itself. So, `Application` class depends on the abstraction rather than the concrete implementation detail.

The `BureauDataProvider` class in `BureauData` module implements `IApplicationBureauDataProvider` from `Mortgage` module. So, the detail implementation class implements(depends on) the abstraction forced by higher level module.

Similarly, `BureauDataProvider` depends on `IDataCleaner` interface defined in `BureauData` module and `DataCleaner` class in `Utility` module is implementing `IDataCleaner` interface.


As you can see, the advantage of this design is that the changes to `BureauDataProvider` cannot affect `Application` because it uses interface `IApplicationBureauDataProvider` which will still be preserved. Also, we can easily reuse `Application` class with another bureau data provider as long as the new bureau data provider implements `IApplicationBureauDataProvider`.


{{% notice note %}}
It is not necessary that the interfaces higher level module depend on should be packaged in the same module. It can be in different module as long it is owned by the higher level module (i.e. changed only when needed for higher level module).
{{% /notice %}}
