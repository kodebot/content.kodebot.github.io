---
title: "Liskov Substitution Principle"
date: 2019-02-22T10:25:49Z
weight: 4
draft: false
---

Barbara Liskov introduced this principle and she says

> What is wanted here is something like the following substitution property: If for each object o1 of type S there is an object o2 of type T such that for all programs P defined in terms of T, the behaviour of P is unchanged when o1 is substituted for o2 then S is a subtype of T.

Let's understand this with an example. Suppose we have a class `MusicPlayer` and its subtype `TrialMusicPlayer`

``` csharp
public class MusicPlayer
{
    public virtual void Play()
    {
        // play song
    }

    public virtual void SkipNext()
    {
        // play next song
    }
}
```

``` csharp
public class TrialMusicPlayer : MusicPlayer
{
    public override void Play()
    {
        // play song for 30 seconds
    }

    public override void SkipNext()
    {
        throw new Exception("Skip next feature is not available in Trial player");
    }
}
```


explain what is Liskov Substitution Principle

example for class that doesn't follow Liskov Substitution Principle

list the problems it causes

show how it can be refactored to adhere to Liskov Substitution Principle

Contravariance of method arguments in subtype - if parent takes list of Animal, the subtype cannot take list of Cat
Covariance of return types in the subtype
No new exception from the method (except the subtype of the exception thrown by base class)


Preconditions cannot be strengthened in a subtype.
Postconditions cannot be weakened in a subtype.
Invariants of the supertype must be preserved in a subtype.
History constraint (the "history rule") - adding new method only in subtype that allows state change


### References

https://en.wikipedia.org/wiki/Liskov_substitution_principle

https://www.hpl.hp.com/techreports/90/HPL-90-121.pdf