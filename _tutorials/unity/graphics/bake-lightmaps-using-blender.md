---
# BASICS
id       : tGraphicsBlenderLightmapping
title    : "Baking lightmaps using Blender"
date     : 2015-11-15
author   : aStardog

subtitle       : "How to bake lightmaps using Blender and bring them into Unity!"
subtitle-short : "How to bake lightmaps using Blender and bring them into Unity!"

# IMAGES
bg-img-path  : "main.png"
bg-img-scale : 180%

# OPTIONS - TUTORIAL
isAvailable    : true
type           : graphics
rel-tutorials  : [tParty, tHealth]
rel-references : [rInheritance, rClass]

# OPTIONS - GENERAL
isHidden : false
---
Here's how to bake lightmaps using Blender and bring them into Unity!

<img src="{{ site.baseurl }}{{ site.url-imgs }}{{ page.url }}main.png" alt="Final lightmapped scene with two objects.">

<video width="100%" height="200" controls loop video controls autoplay>
	<source src="movie.mp4" type="video/mp4">
	<source src="movie.ogg" type="video/ogg">
	Your browser does not support the video tag.
</video>

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