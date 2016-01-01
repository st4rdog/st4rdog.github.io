---
# BASICS
id       : rDeltaTime
title    : "deltaTime"
date     : 2015-11-02
subtitle : "How to use deltaTime when making your game."
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
**deltaTime** allows your game to be frame-rate independent. It's a small number that changes based on the user's frame-rate. It's **0.01666** at 60fps, or **0.333** at 30fps.

Multiplying by this number will make sure things happen in **units per second**, instead of **frames per second**.

## When to Use?

Usually when you have code that needs to do something over time.

* A camera following an object.
* ...

## Examples

...

## Notes

* http://forum.unity3d.com/threads/the-truth-about-fixedupdate.231637/#post-2442966
* http://fabiensanglard.net/timer_and_framerate/index.php