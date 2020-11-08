---
# BASICS
refid    : rLighting
title    : "Lighting"
date     : 2015-11-02
subtitle : "How to setup good lighting in Unity."
author   : aStardog

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%
icon-fa-id  : f185

# OPTIONS - REFERENCE
isAvailable    : true
type           : graphics
rel-tutorials  : [tGraphicsBlenderLightmapping]
rel-references : [rLightmapping, rGlobalIllumination, rGraphicsOptimisation]

# OPTIONS - GENERAL
isPublic     : true
showComments : true
---
Here are some useful **lighting** setups for Unity 5.

* TOC
{:toc}

## Lighting styles in Unity

As of Unity 5.6, these are the current options you have for lighting your game.

### Fully Realtime

...

#### Pros

* Shadows can move in-game.
* Dynamic objects look no different to static geometry.
* No need to spend hours baking lightmaps.
* Great for procedurally generated games.

#### Cons

* Realtime shadows are bad for performance.
  * Shadow calculation and increased draw calls on objects casting shadows.
  * Will not run smoothly (or at all) on older platforms.
* Realtime shadows lack the softness of baked shadows.
* Shadow quality degrades with a larger shadow distance.
  * To keep shadows sharp up close, [there will be no shadows past a certain distance.](https://youtu.be/Xz6V5dizojE?t=12s), and you will have to adjust [Shadow Cascades](https://docs.unity3d.com/Manual/DirLightShadows.html).
* No Global Illumination (indirect light bounces). See 'Fully Realtime (with Precomputed Realtime GI)'.

### Fully  Baked

...

#### Pros

* Great performance on many devices, including old phones/tablets, and old PC's.
* Global Illumination (indirect light bounces).
* Shadows can be softened to create [penumbras](https://en.wikipedia.org/wiki/Umbra,_penumbra_and_antumbra).

#### Cons

* Shadows cannot be moved in-game.
* Long bake times.
* Dynamic objects can look different to baked geometry.
  * Dynamic objects are lit by Light Probes, so can often seem 'seperate' from static geometry.
  * Dynamic objects lack shadows.
  * Leads to dynamic doors being unable to block light between rooms.
* Not usually useable for procedurally generated games.
  * It's possible to bake lightmaps onto prefabs, and instantiate them as modular pieces.

### Fully Realtime (with Precomputed Realtime GI)

Precomputed Realtime GI adds realistic indirect lighting to realtime lights.

#### Pros

* Realistic light bounces while being able to move the lights/shadows.

#### Cons

* It's a high-end feature, so will have a performance impact.
* Needs to be precomputed/baked in the editor.
  * Not useable for procedurally generated games.
  * Dynamic situations, such as walls breaking, will not update the GI to reflect the changes.

### Mixed - Baked Indirect

...

#### When to use?

...

### Mixed - Distance Shadowmask

...

#### When to use?

...

### Mixed - Shadowmask

...

#### When to use?

...

### Mixed - Subtractive

...

#### When to use?

...

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
* Light probes for dynamic objects
* Ambient Source set to Color

### Half-life 2
* Baked GI only
* Most lights set to Baked
* Some lights set to Mixed (so dynamic objects will cast real-time shadows on top of static)
* Light probes for dynamic objects
* Ambient Source set to Color

### Doom 3
* Baked GI and Precomputed Realtime GI both off
* Lights set to Realtime, some casting shadows
* Light probes for dynamic objects
* Ambient Source set to Color

### Skyrim, Fallout 4
* Baked GI and Precomputed Realtime GI both off
* Lights set to Realtime, some casting shadows
* No light probes
* Ambient Source set to Color/Gradient

### Bloodborne
* Baked GI and Precomputed Realtime GI both off
* Lights set to Realtime, some casting shadows
* No light probes
* Ambient Source set to Color/Gradient

## Notes

* These are all rough dates.
* When exporting to WebGL/Mobile, you currently (May 2017) have to use Gamma Color Space.
* https://unity3d.com/learn/tutorials/modules/beginner/graphics/lighting-and-rendering
* https://unity3d.com/learn/tutorials/topics/graphics/starting-precompute-process
* https://unity3d.com/learn/tutorials/projects/creating-believable-visuals/lighting-strategy?playlist=50020
* https://blogs.unity3d.com/2018/08/28/spotlight-team-best-practices-setting-up-the-lighting-pipeline/