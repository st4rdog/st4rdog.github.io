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
rel-references : [rProgrammingOptimisation]

# OPTIONS - GENERAL
isHidden : false
---
<a href="http://docs.unity3d.com/ScriptReference/Time-deltaTime.html" class="external">**deltaTime**</a> allows your game to be frame-rate independent. It's the time in seconds it took to complete the last frame.

* **0.01666** at 60fps (1 divided by 60)
*  **0.33333** at 30fps

Multiplying by this number will make sure things happen in **units per second**, instead of **units per frame**.

## When to Use?

Usually when you have code that needs to do something over time.

* Moving any object over time.

## Examples

...

## Notes

* http://docs.unity3d.com/ScriptReference/Time-deltaTime.html
* http://forum.unity3d.com/threads/the-truth-about-fixedupdate.231637/#post-2442966
* http://fabiensanglard.net/timer_and_framerate/index.php