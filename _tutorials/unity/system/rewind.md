---
# BASICS
id       : tRewind
title    : "Rewind Time"
date     : 2015-11-02
subtitle : "How to rewind time in-game to correct mistakes"
author   : aStardog

# IMAGES
bg-img-path  : "/imgs/rockettournament/001.png"
bg-img-scale : 250%

# OPTIONS - TUTORIAL
isAvailable : true
type        : system

# OPTIONS - GENERAL
isHidden : false
---
To rewind your game, all you have to do is track/log the <a href="http://docs.unity3d.com/ScriptReference/Transform-position.html">positions</a> of everything that you want to be rewindable.

## Outline

We need a Rewindable script on every GameObject that should track its position.

We also need a RewindManager script that will initiate the rewind.

* **Rewindable.cs**
  * **Variables**
    * Positions
  * **Functions**
    * ...

* **RewindManager.cs**
  * **Variables**
	* IsRunning
	* CurrentStep
	* MaxStep
  * **Functions**
    * Begin
	* Stop

<script src="https://gist.github.com/st4rdog/e2106ebfde1f7ba93d5d.js"></script>

<script src="https://gist.github.com/st4rdog/443c828441146fc7c2ff.js"></script>