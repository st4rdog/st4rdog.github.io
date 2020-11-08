---
# BASICS
refid    : rProgrammingOptimisation
title    : "Optimising Code"
date     : 2015-11-02
subtitle : "How to optimize your code."
author   : aStardog

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%
icon-fa-id   : f3fd

# OPTIONS - REFERENCE
isAvailable    : false
type           : programming
rel-tutorials  : 
rel-references : [rGraphicsOptimisation, rDeltaTime]

# OPTIONS - GENERAL
isPublic     : true
showComments : true
---
{{ page.title }} reference page.

* TOC
{:toc}

## Update()

Do not do anything "heavy" inside Update.

## Camera.main

Camera.main is doing <code>GameObject.FindObjectWithTag("MainCamera");</code> every time it's called.

* ~9m30s [Unite Europe 2017 - Squeezing Unity: Tips for raising performance](https://www.youtube.com/watch?v=_wxitgdx-UI)

## Garbage Collection

...

## Notes

* https://forum.unity3d.com/threads/looking-for-some-general-performance-optimization-tips.286837/
* Garbage Collection
  * https://docs.unity3d.com/Manual/UnderstandingAutomaticMemoryManagement.html
  * https://www.reddit.com/r/Unity3D/comments/6dh9mt/things_i_learnt_today_gc/
* https://docs.unity3d.com/ScriptReference/Transform.SetPositionAndRotation.html
* https://blogs.unity3d.com/2017/06/29/best-practices-from-the-spotlight-team-optimizing-the-hierarchy/
* https://www.youtube.com/watch?v=mQ2KTRn4BMI&feature=youtu.be&t=44m10s (~48m never use instantiate at runtime, never use Update/FixedUpdate - use custom Tick() function called by a script that finds/collects all scripts on start)
* https://forum.unity3d.com/threads/so-how-am-i-supossed-to-know-or-learn-these-things.480987/
* https://docs.unity3d.com/Manual/webgl-memory.html
* [Unite Europe 2017 - Squeezing Unity: Tips for raising performance](https://www.youtube.com/watch?v=_wxitgdx-UI)
* [Unity Scene Hierarchy: Catch that Performance Thief! Part 2](https://www.gamasutra.com/blogs/RubenTorresBonet/20191121/354452/Unity_Scene_Hierarchy_Catch_that_Performance_Thief_Part_2.php)