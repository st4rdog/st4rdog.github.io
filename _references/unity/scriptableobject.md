---
# BASICS
refid    : rScriptableOject
title    : "ScriptableObject"
date     : 2017-5-31
subtitle : "How to use ScriptableObjects when making your game."
author   : aStardog

# IMAGES
bg-img-path  : "001.png"
bg-img-scale : 150%

# OPTIONS - REFERENCE
isAvailable    : false
type           : unity
rel-tutorials  : 
rel-references : 
complexity     : 5

# OPTIONS - GENERAL
isPublic : true
---
**ScriptableObjects** is a class you can derive from if you want to create objects that don't need to be attached to game objects.

This is most useful for assets which are only meant to store data. They can act like "profile" or "config" data.

To make it easy to create ScriptableObject instances that are bound to assets in your project, see CreateAssetMenuAttribute.

* TOC
{:toc}

## Examples

### Player Movement Profile/Configuration

Walk/Run speed settings...

https://www.cleverous.com/single-post/2016/05/25/Interfaces-and-ScriptableObjects-1

### Video Settings - High, Medium and Low

https://www.cleverous.com/single-post/2016/05/25/Interfaces-and-ScriptableObjects-1

## Official Unity Tutorials

* [Live Training 16th February 2016 - Introduction to Scriptable Objects](https://www.youtube.com/watch?v=9gscwiS3xsU)
* [Live Training 8th August 2016 - Ability System with Scriptable Objects](https://www.youtube.com/watch?v=bvRKfLPqQ0Q)

## Notes

* https://docs.unity3d.com/ScriptReference/ScriptableObject.html
* [Unite Europe 2016 - Overthrowing the MonoBehaviour tyranny in a glorious ScriptableObject revolution](https://www.youtube.com/watch?v=VBA1QCoEAX4)
* http://www.gamasutra.com/blogs/AsadSohail/20170530/298869/Unity_Editor_Scripting_A_kickstarter_guide__Part_3.php
* https://www.cleverous.com/single-post/2016/05/25/Interfaces-and-ScriptableObjects-1
* [ScriptableObjects As A Database Example In Unity 5](https://www.youtube.com/watch?v=1cC04hUbiM0)
* [Scriptable Object event system](https://unity3d.com/how-to/architect-with-scriptable-objects#cool-things)
* [GameDev Architecture - Scriptable Object Events With Custom Data - Unity - Part 2](https://www.youtube.com/watch?v=P-U7GPXMtLY)
* [Stop Using Singletons With Runtime Set ScriptableObjects](https://www.youtube.com/watch?v=Wo2qQPqfYJs)