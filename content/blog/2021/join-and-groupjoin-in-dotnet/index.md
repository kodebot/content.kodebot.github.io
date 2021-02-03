---
title: "Join and GroupJoin in C#"
date: 2021-02-03T13:55:27Z
draft: false
disableBreadcrumb: true
tags: ["C#", ".NET"]
categories: []
comments: true
---

### Introduction
`Join` and `GroupJoin` are two different methods that we can use in our LINQ query to join two different collections. At first glance, they might look similar but they produce different results. Lets look at how they work with an example.

### Example setup
For our example, we are going to use the following `Student` and `Enrolment` class.

```csharp
class Student
{
    public string Id { get; set; }
    public string Name { get; set; }
}

class Enrolment
{
    public string Id { get; set; }
    public string StudentId { get; set; }
}
```
And we assume, we have the following data
```csharp
var students = new List<Student>
{
    new Student {Id = "s1", Name = "Foo"},
    new Student {Id = "s2", Name = "Bar"},
    new Student {Id = "s3", Name = "Cux"}
};

var enrolments = new List<Enrolment>
{
    new Enrolment {Id = "e1", StudentId = "s1"},
    new Enrolment {Id = "e2", StudentId = "s1"},
    new Enrolment {Id = "e1", StudentId = "s2"},
};
```
Here, student `s1` has more than one enrolments and `s2` has one enrolment and `s3` has none.

### Join
`Join` basically creates a new collection by taking each item from first collection and combining it with each item on the second collection where the join conditions are met.

For example,
```csharp
students.Join(
    enrolments,
    s => s.Id,
    e => e.StudentId,
    (s, e) => new { Student = s.Id, Enrolment = e.Id });

```
Query version
```csharp
from s in students
join e in enrolments
on s.Id equals e.StudentId
select new { Student = s.Id, Enrolment = e.Id };
```
produces
```json
[
  {
    "Student": "s1",
    "Enrolment": "e1"
  },
  {
    "Student": "s1",
    "Enrolment": "e2"
  },
  {
    "Student": "s2",
    "Enrolment": "e1"
  }
]

```
Here, we have two items for student `s1` because `s1` has two enrolments, one item for `s2` and no item for `s3` as `s3` has no enrolments.

This very similar to inner join in SQL.

### GroupJoin
`GroupJoin` takes each item from the first collection, finds all items from the second collection where join conditions are met and combines them. This means, the result collection will have same number of entries as first collection and each item from the first collection may have zero or more associated items from second collection.

For example,

```csharp
students.GroupJoin(
    enrolments,
    s => s.Id,
    e => e.StudentId,
    (s, es) => new { Student = s.Id, Enrolments = es.Select(e => e.Id) });

```
Query version
```csharp
from s in students
join e in enrolments
on s.Id equals e.StudentId into joined
select new { Student = s.Id, Enrolment = joined.Select(j => j.Id) };
```
produces
```json
[
  {
    "Student": "s1",
    "Enrolments": [
      "e1",
      "e2"
    ]
  },
  {
    "Student": "s2",
    "Enrolments": [
      "e1"
    ]
  },
  {
    "Student": "s3",
    "Enrolments": []
  }
]
```
Here, we have three items in the result collection - same number of items as first collection(one for each student). But, `s1` has two enrolments, `s2` has one and `s3` has no enrolments. Note, even though there is no matching enrolment for `s3`, we still have it in the result but no items in enrolments.

This is similar to left outer join in SQL.
