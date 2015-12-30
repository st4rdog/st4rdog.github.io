---
# BASICS
id       : tHealth
title    : "Health"
date     : 2015-11-02
subtitle : "How to make a health system so something can take damage"
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
...

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