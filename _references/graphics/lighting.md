---
# BASICS
id       : rLighting
title    : "Lighting"
date     : 2015-11-02
subtitle : "How to setup good lighting in Unity."
author   : aStardog

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%

# OPTIONS - REFERENCE
isAvailable    : true
type           : graphics
rel-tutorials  : [tGraphicsBlenderLightmapping]
rel-references : [rLightmapping, rGraphicsOptimisation]

# OPTIONS - GENERAL
isHidden : false
---
Here are some useful **lighting** setups for Unity 5.

* TOC
{:toc}

## Lighting styles by year

These dates refer to the rough cut-off points where the latest PC games started moving towards that style of lighting. For example, vertex lighting did not stop being used in 1996, in fact, it's used to this very day, and most PS2 games used it.

### 1995-before
* Precomputed GI/Baked GI both off
* Lights set to Realtime, no shadows
* Ambient Source set to Color
* Edit > Project > Player > Legacy Vertex Lit, Gamma color

### 1996-2002 lighting (Half-life 1, Quake 3, etc)
* Baked GI on only
* Lights set to Baked
* Ambient Source probably Color
* Forward rendering, Gamma color

### 2003/4+ lighting (Doom 3, Thief 3, Bioshock)
* Precomputed GI/Baked GI both off
* Lights set to Realtime, few casting shadows
* Ambient Source set to Color
* Doom 3 used Forward rendering with Gamma colors, I assume

### ~2008+ lighting (Battlefield Bad Company 2, etc)
* As above, but Deferred/Linear rendering.

### 2015+ lighting
* Precomputed GI on
* Baked GI off
* Lights set to Realtime, some casting shadows
* Ambient Source Skybox or Gradient
* Usually PC games will use Deferred/Linear.

## Lighting styles by console

Listed are the "best" styles of lighting these consoles are computationaly capable of.

### PS2
* ...

### Xbox
* ...

### PS3/Xbox 360
* ...

### PS4/Xbox One
* ...

## Lighting styles by game

Here are the settings you can use in Unity to replicate these games.

### Quake/Half-life
* Baked GI only
* All lights set to Baked
* Ambient Source set to Color

### Half-life 2
* Baked GI only
* Most lights set to Baked
* Some lights set to Mixed, so dynamic objects will cast real-time shadows on top of static.
* Ambient Source set to Color

### Doom 3
* Baked GI and Precomputed Realtime GI both off.
* Most lights set to Realtime, some casting shadows.
* Ambient Source set to Color

### Skyrim
* Baked GI and Precomputed Realtime GI both off.
* Most lights set to Realtime, some casting shadows.
* Ambient Source set to Color

### Bloodborne
* Baked GI and Precomputed Realtime GI both off.
* Most lights set to Realtime, some casting shadows.
* Ambient Source set to Color

## Notes

* These are all rough dates.
* When exporting to WebGL/Mobile, you currently (2016) have to use Gamma Color Space.
