---
title: "TPL Task and Windows Identity Impersonation - The beauty of Closure"
date: 2015-04-09T00:00:00+00:00
publishdate: 2015-04-09T00:00:00+00:00
lastmod: 2015-04-09T00:00:00+00:00
tags: ["C#"]
disableNextPrev: true
hidden: true
comments: true
draft: false
---

<p>I have created a web application with Windows Authentication and impersonation is enabled as I need the application connect to SQL Server database using Windows Authentication.</p>
<p>I wanted&nbsp;to run a TPL task in the impersonated context, so, I added the following code naively in a&nbsp;action method of one of my controllers</p>

```cs
// naive task code

Task.Run(() =>
{
      // Task code here
});

```

<p>Though, <a href="https://social.msdn.microsoft.com/Forums/vstudio/en-US/a1da0143-919c-433d-9d50-83795879082d/tasks-and-impersonation?forum=parallelextensions" target="_blank">this answer</a>&nbsp;suggests that tasks will run under the same context under which it was created, it wasn't working that way in my case.</p>
<p>The task is created under impersonated context but the task was invoked under the identity configured in application pool which is network service in this case.&nbsp;</p>

To make this work, I need to invoke the method in the task under impersonated context. The easiest way is to capture the `WindowsIdentity` and make it available to the task function so it can execute any code under the impersonated&nbsp;context.

<p>The Closure feature helped me to achieve this elegantly. &nbsp;This means, lambda expressions or lambda functions can access any variables declared in the block where the lambda expressions or lambda functions&nbsp;are defined. So, I created a local variable in my action method and used in the task function to run code under the impersonated context. Here is the sample code</p>

```js
// Task using closure
var currentWindowsIdentity = WindowsIdentity.GetCurrent();
Task.Run(() =>
{

    using (currentWindowsIdentity.Impersonate())
    {
        // Task code here
    }

});
```
