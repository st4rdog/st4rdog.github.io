---
# BASICS
id       : rCommunication
title    : "Communication"
date     : 2015-11-02
subtitle : "How to communicate between scripts/components/classes."
author   : aStardog

# IMAGES
bg-img-path  : "/imgs/tutorials/game/monster-catcher/001.jpg"
bg-img-scale : 250%

# OPTIONS - REFERENCE
isAvailable    : true
type           : programming
rel-tutorials  : 
rel-references : 

# OPTIONS - GENERAL
isHidden : false
---
Communication between scripts/classes/components is important in Unity.

Classes often need to look at other Classes to see what they're doing, or react when something changes elsewhere, or run a Function inside another Class.

## Reference

The main way to access another Class/Component is to reference an Instance of it.

This requires you to find it in the scene, or create a new one from scratch.

This means you create a public variable...

[TODO: Mention GameObject.Find...]

##Events & Delegates

Events & Delegates allow your code to react when something happens.

###Events

...

#### Examples

* EnemyDied
    * The enemy will play its death animation.
    * The players' score will increase.
* ScoreIncreased
    * The GUI will update the score display.
* DialogStarted
    * The GUI will appear when it hears this.

### Delegates

A Delegate is like a variable that holds a list of Functions.

This allows you to call multiple Functions at once.

### Action

Delegate and Event combined.

### Callback

...

### Game Use Cases

...

## UnityEvents

...

###Code

using UnityEngine.Events;

public UnityEvent _eventName;

## Singletons

Singletons are a class that references itself, and can be accessed via this reference variable.

Because the variable is Static, it can be accessed like ClassName.InstanceVariable from any other class, instead of having to find the instance in the scene via Find/etc.

### Notes

* Should rarely be used in Unity
    * http://answers.unity3d.com/questions/551297/how-can-i-instantiate-a-prefab-from-a-static-funct.html
        * http://answers.unity3d.com/answers/551350/view.html
        * Better Version of Grid system:
            * http://answers.unity3d.com/questions/552780/singleton-usage-wherever-possible.html
        * Better Version again (Verfices)
            * http://forum.unity3d.com/threads/verfices-a-well-written-clean-documented-and-optimized-global-access-system.210080
            * http://pastebin.com/n1SSE3h3
