---
# BASICS
id     : tRewind
title  : "Rewind Time"
date   : 2015-11-02
author : aStardog

subtitle       : "How to rewind time in-game to correct mistakes"
subtitle-short : "How to rewind time in-game to correct mistakes"

# IMAGES
bg-img-path  : "/imgs/tutorials/game/survival-game/001.png"
bg-img-scale : 180%

# OPTIONS - TUTORIAL
isAvailable    : true
type           : system
rel-tutorials  : 
rel-references : [rClass]

# OPTIONS - GENERAL
isHidden : false
---
To rewind your game, all you have to do is track/log the <a href="http://docs.unity3d.com/ScriptReference/Transform-position.html" class="external">positions</a> of everything that you want to be rewindable.

* TOC
{:toc}

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