---
# BASICS
id       : tParty
title    : "RPG Party"
date     : 2015-11-02
author   : aStardog

subtitle       : "How to make an RPG Party with party members"
subtitle-short : "How to make an RPG Party with party members"

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
Here's how to make a simple Party script.

* TOC
{:toc}

## Intro

A party is simply a list of people who are in that party. It needs to have functions that can add/remove members.

* **Party.cs**
  * **Variables**
    * Members
  * **Functions**
    * Add
    * Remove
  * **Events**
    * Added
    * Removed

<script src="https://gist.github.com/st4rdog/0cd8e3253e1e9ab3d462.js"></script>

<script src="https://gist.github.com/st4rdog/62e34a1c4908ab608bb6.js"></script>