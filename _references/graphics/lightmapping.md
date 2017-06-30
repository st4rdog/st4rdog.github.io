---
# BASICS
refid    : rLightmapping
title    : "Lightmapping"
date     : 2015-11-02
subtitle : "What are lightmaps? And how to use them when making your game."
author   : aStardog

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%

# OPTIONS - REFERENCE
isAvailable    : true
type           : graphics
rel-tutorials  : [tGraphicsBlenderLightmapping]
rel-references : [rLighting, rGlobalIllumination, rGraphicsOptimisation]

# OPTIONS - GENERAL
isPublic     : true
showComments : true
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

## Pros &amp; Cons

### Pros

* Good in-game performance because the lighting/shadows were calculated in advance.
* Time spent calculating lighting/shadows offline can equate to more realistic lighting in-game.
* Allows for bounced lighting. (Note: Unity 5+ can do real-time bounced with Pre-Computed GI)

### Cons

* Time-consuming.
* Uses up memory, depending on quality/resolution.
* For static geometry only. Cannot be updated in real-time or generated in-game. Opening/closing doors will be a problem.
* Dynamic objects can sometimes "stand out" from lightmapped geometry. They have to be lit seperately by Light Probes.
* Increases file size of application.

## History of lightmapping in video games

TODO: Link to lighting reference page...
Quake was the first game to use lightmaps.

## Notes

* http://polycount.com/discussion/76554/lightmaps-tech-pros-and-cons
* https://unity3d.com/learn/tutorials/topics/graphics/starting-precompute-process
* https://unity3d.com/learn/tutorials/topics/graphics/introduction-precomputed-realtime-gi (Added 19 May 2017)