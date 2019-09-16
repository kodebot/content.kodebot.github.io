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
}
```

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

We have another class `PlayerWidget`. This class represents a type of user interface that user can use to control the media playback and it simply delegates user requests to the `MusicPlayer`.

``` csharp
public class PlayerWidget
{
    private readonly MusicPlayer _player;
    public PlayerController(MusicPlayer player)
    {
        _player = player;
    }

    public void PlayButtonPressed()
    {
        _player.Play();
    }
}
```

The essence of Liskov Substitution Principle is that we should be able to use objects of derived type in place of objects of base type without altering the behaviour of the program that is using those objects

In this example, `TrialMusicPlayer` is not qualified to be subtype of `MusicPlayer` because, we cannot substitute the object of `TrialMusicPlayer` for the object of `MusicPlayer` without changing (or breaking) `PlayerWidget`. This is because `PlayerWidget` is not built to handle the new exception thrown by `TrialMusicPlayer` when more than 5 songs are played.

There are many subtle ways in which we can break this substitutability. 

The following are the general rules to follow to avoid breaking substitutability

* No new exception from any method in the subtype. However, we can throw new exception which is subtype of the exception thrown by base class.

* Contravariance of method arguments in subtype - if parent takes list of Animal, the subtype cannot take list of Cat

* Covariance of return types in the subtype

* Preconditions cannot be strengthened in a subtype

* Postconditions cannot be weakened in a subtype

* Invariants of the supertype must be preserved in a subtype

* History constraint (the "history rule") - adding new method only in subtype that allows state change


### References

https://en.wikipedia.org/wiki/Liskov_substitution_principle

https://www.hpl.hp.com/techreports/90/HPL-90-121.pdf