---
# BASICS
refid    : tHealth
title    : "Health"
date     : 2015-11-02
author   : aStardog

subtitle       : "How to program a health system so something can take damage!"
subtitle-short : "How to program a health system so something can take damage!"

# IMAGES
bg-img-path        : "potion.PNG"
bg-img-scale       : 50%
bg-img-scale-hover : 70%

# OPTIONS - TUTORIAL
isAvailable    : true
type           : system
rel-tutorials  : [tHealthBar]
rel-references : [rClass]

# OPTIONS - GENERAL
isPublic : true
---
Health in games is very simple. In Unity, it's as easy as getting a <a href="{{ site.url }}{{ site.url-references-unity }}gameobject">GameObject</a>'s Health <a href="{{ site.url }}{{ site.url-references-unity }}component">Component</a>, then calling the <a href="{{ site.url }}{{ site.url-references-programming }}class">Function</a> that removes the health.

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