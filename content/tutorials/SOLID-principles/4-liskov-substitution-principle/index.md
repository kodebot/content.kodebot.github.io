---
title: "Liskov Substitution Principle"
date: 2019-9-18T00:00:00Z
weight: 4
draft: false
---

Liskov Substitution Principle(LSP) is about substitution of one object for another without affecting the program that uses those objects.

[Barbara Liskov](https://en.wikipedia.org/wiki/Barbara_Liskov) introduced this principle and she says

> What is wanted here is something like the following substitution property: If for each object o1 of type S there is an object o2 of type T such that for all programs P defined in terms of T, the behaviour of P is unchanged when o1 is substituted for o2 then S is a subtype of T.

Let's understand this with an example. 

Suppose we have a class `MusicPlayer` which allows users to play music

``` csharp
public class MusicPlayer
{
    public virtual void Play()
    {
        // play song
    }
}
```

We have `TrialMusicPlayer` which is inherited from `MusicPlayer` class

``` csharp
public class TrialMusicPlayer : MusicPlayer
{
    public override void Play()
    {
        if(_songsPlayedToday >= 5)
        {
            throw new Exception("Skip next feature is not available in Trial player");
        }

        // play song
    }
}
```

`TrialMusicPlayer` class overrides `Play()` method to allow playing only 5 songs a day.

We have another class `PlayerWidget`.

``` csharp
public class PlayerWidget
{
    private readonly MusicPlayer _player;
    public PlayerWidget(MusicPlayer player)
    {
        _player = player;
    }

    public void PlayButtonPressed()
    {
        _player.Play();
    }
}
```
 This class represents one of the user interfaces that user can use to control the music player and it simply delegates user requests to the `MusicPlayer`.

{{% img "images/LSP.png" "" 250 %}}


The essence of Liskov Substitution Principle is that we should be able to use objects of derived type in place of objects of base type without altering the behaviour of the program that is using those objects, only then we can call the derived type as **subtype**.

In this example, `TrialMusicPlayer` is not qualified to be subtype of `MusicPlayer` because, we cannot substitute the object of `TrialMusicPlayer` for the object of `MusicPlayer` without changing (or breaking) `PlayerWidget`. This is because `PlayerWidget` is not built to handle the new exception thrown by `TrialMusicPlayer` when more than 5 songs are played.

There are many subtle ways in which we can break substitutability of objects. 

The following are the general rules to follow to avoid breaking substitutability

#### No new exception
No new exception from any method in the subtype. However, we can throw new exception which is subtype of the exception thrown by base class. This is because the exception handler of a type will handle the exceptions of derived exception type as well.

#### Contravariance of method arguments in subtype
{{%box tip %}}

Just to give brief introduction on **variance**. [Wikipedia](https://en.wikipedia.org/wiki/Covariance_and_contravariance_(computer_science)) says

<cite>Variance refers to how subtyping between more complex types relates to subtyping between their components</cite>

Let's try to understand this with examples. We will assume that we have a base class `Person`. We have another class `Employee` which is derived from `Person`. Variance comes into picture when we have complex type with one or more independent type components. Generics is one such complex, so we will use generic type `List<T>` in our examples

If `List<Person>` is substitutable for `List<Employee>` then `List<T>` is **covariant**

If `List<Employee>` is substitutable for `List<Person>` then `List<T>` is **contravariant**

If `List<Person>` is substitutable for `List<Employee>` and `List<Employee>` is substitutable for `List<Person>` then `List<T>` is **bivariant**

If `List<Person>` and `List<Employee>` are not substitutable for each other then `List<T>` is **invariant**

**Note:** there is lot more to understand about _variance_, we covered just enough in the context of Liskov Substitution Principle

{{%/box%}}

The method arguments in subtype must must be contravariant to preserve substitutability

#### Covariance of return type in subtype
Return types in the subtype must be covariant

#### Preconditions
Preconditions are any validation that we perform before executing a method and it should be strengthened in a subtype

#### Postconditions
Postconditions are any validation that we perform after the method is executed and it should not be weakened in a subtype

#### Invariants
Invariant refers to properties or states that are preserved when method is executed and any such invariants of supertype must be preserved in a subtype

{{%notice info%}}
What we refer as **invariant** is different from the one we have see as part of **variance** above. You can learn more about **Precondiations**, **Postconditions** and **invariants** [here](https://en.wikipedia.org/wiki/Design_by_contract).
{{% /notice%}}

#### History constraint
Subtype should not introduce a new method that allows mutating state that is immutable in supertype

### References

1. https://en.wikipedia.org/wiki/Liskov_substitution_principle

2. https://www.hpl.hp.com/techreports/90/HPL-90-121.pdf

3. [Covariance and Contravariance - Wikipedia](https://en.wikipedia.org/wiki/Covariance_and_contravariance_(computer_science))