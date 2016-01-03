---
# BASICS
id       : rLightmapping
title    : "Lightmapping"
date     : 2015-11-02
subtitle : "What are lightmaps? And how to use them when making your game."
author   : aStardog

# OPTIONS - REFERENCE
isAvailable    : true
type           : graphics
img            : ""
rel-tutorials  : [tGraphicsBlenderLightmapping]
rel-references : [rProgrammingOptimisation, rGraphicsOptimisation]

# OPTIONS - GENERAL
isHidden : false
---
Lightmaps exist to allow highly detailed shadows/light that will run smoothly on low-end hardware.

* TOC
{:toc}

## When to Use?

* You want **shadows**, but are targetting devices that don't have the CPU/GPU power to compute them in real-time.
  * Mobile games.
  * F2P PC games that require lot of users.
* You want **better quality lighting** than real-time lighting can currently deliver.
  * Unity 5's Precomputed GI tries to bridge this gap by allowing real-time light bounces.

## How does it work?

A lightmap is a texture that contains lighting information.

Light is precalculated (baked) then layered on top of your main textures.

They are stored in memory when a level is loaded, so no CPU usage is required to display the lighting.

### Notes

* Traditional lightmapping requires the lightmap to be "layered" on top of a diffuse map.

## History of lightmapping in video games

Quake was the first game to use lightmaps.