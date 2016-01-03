---
# BASICS
id       : tHealth
title    : "Health"
date     : 2015-11-02
author   : aStardog

subtitle       : "How to make a health system so something can take damage!"
subtitle-short : "How to make a health system so something can take damage!"

# IMAGES
bg-img-path  : "/imgs/tutorials/game/survival-game/001.png"
bg-img-scale : 180%

# OPTIONS - TUTORIAL
isAvailable    : true
type           : system
rel-tutorials  : 
rel-references : 

# OPTIONS - GENERAL
isHidden : false
---
...

* TOC
{:toc}

## Outline

We need a variable to hold our health and a function that removes health.

We should send an event whenever we are hit, and also an event when we are dead.

* **Health.cs**
  * **Variables**
    * CurrentHP
	* MaxHP
  * **Functions**
    * TakeDamage
  * **Events**
    * Hit
	* Died