---
# BASICS
id       : tGraphicsBlenderLightmapping
title    : "Baking lightmaps using Blender"
date     : 2015-11-15
author   : aStardog

subtitle       : "How to bake lightmaps using Blender and bring them into Unity!"
subtitle-short : "How to bake lightmaps using Blender and bring them into Unity!"

# IMAGES
bg-img-path  : "/imgs/tutorials/game/resi/001.png"
bg-img-scale : 180%

# OPTIONS - TUTORIAL
isAvailable : true
type        : graphics

# OPTIONS - GENERAL
isHidden : false
---
Here's how to bake lightmaps using Blender and bring them into Unity!

## Summary

Here's a quick rundown of how to do it.

* ...
    * ...

## Create objects for baking

...

## UV Unwrapping

...

## Create empty material

...

## Bake Ambient Occlusion

...

## Bake final texture

...

## Notes

* It's important to have the correct object selected when doing things. Blender is context/selection sensitive.
    * To apply an image to faces, you must have the faces selected in Edit mode.
	* When baking, you must have the object selected in Object mode.
* Doesn't work for tiled textures where the mesh's UV's overlap the regular bounds.
    * Tiled texturing works by scaling the UV's to be many times larger than the image. This means they cannot be baked easily.
* https://www.youtube.com/watch?v=3jJGBzAxXKo - Modeling and Texturing a Building in Blender