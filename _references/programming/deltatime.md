---
# BASICS
id       : rDeltaTime
title    : "deltaTime"
date     : 2015-11-02
subtitle : "How to use deltaTime when making your game."
author   : aStardog

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%

# OPTIONS - REFERENCE
isAvailable    : true
type           : programming
rel-tutorials  : 
rel-references : [rProgrammingOptimisation]

# OPTIONS - GENERAL
isHidden : false
---
<a href="http://docs.unity3d.com/ScriptReference/Time-deltaTime.html" class="external">**deltaTime**</a> allows your game to be frame-rate independent. If you do not multiply by deltaTime, you will get different outcomes on different devices.

Time.deltaTime itself is the time in seconds it took to complete the last frame.

* **0.01666** if you are getting 60fps (1 divided by 60)
*  **0.33333** if you are getting 30fps

Multiplying by this number will make sure things happen in **units per second**, instead of **units per frame**.

* TOC
{:toc}

## When to Use?

Usually when you have code that needs to do something over time.

* Moving any object over time.
* Incrementing a number over time.

## Examples

### Moving an object along the X axis

public Transform _cube;

void Update()
{
	// Move the cube 1 unit per frame along the X axis (to the right)
	// If you have a frame-rate of 60, after 1 second, the cube will be at position (60, 0, 0).
	// If you have a frame-rate of 30, after 1 second, the cube will be at position (30, 0, 0).
	// Not good!
	_cube.Translate(1f, 0f, 0f);
	
	// Move the cube 1 unit per second along the X axis (to the right)
	// After 1 second, the cube will be at position (1, 0, 0), regardless of frame-rate. Everyone gets the same result.
	// Good!
	_cube.Translate(1f * Time.deltaTime, 0f, 0f);
}

## Notes

* http://docs.unity3d.com/ScriptReference/Time-deltaTime.html
* http://forum.unity3d.com/threads/the-truth-about-fixedupdate.231637/#post-2442966
* http://fabiensanglard.net/timer_and_framerate/index.php