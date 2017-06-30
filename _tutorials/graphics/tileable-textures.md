---
# BASICS
refid    : tTileableTextures
title    : "Tileable Textures"
date     : 2015-11-15
author   : aStardog

subtitle       : "How to create a tileable/repeatable texture, and remove any lighting and shading from a photo."
subtitle-short : "How to create a tileable texture, and equalize lighting."

# IMAGES
bg-img-path  : "001.png"
bg-img-scale : 180%

# OPTIONS - TUTORIAL
isAvailable    : false
type           : graphics
rel-tutorials  : 
rel-references : 

# OPTIONS - GENERAL
isPublic     : true
showComments : true
---
...

* TOC
{:toc}

## Intro

...

## Tutorial

### How to remove lighting and shading from an image/photo

If you are using a photo texture, sometimes it will have 

- Duplicate Background layer (Ctrl-J)
- On this new layer - Filter > Blur > Average
- Double click Background layer to change it into movable layer.
- Move it to the top of the stack, change it's opacity to 50% and blending mode to Linear Light
- Open Filter > Other > High Pass and play with Radius parameter to control the effect

This texture is now a perfect candidate to be tiled.

### How to make an image/photo tileable

For a game engine, your image should be power of two (2 multiplied by itself n times, e.g. 512x512, 1024x1024, 256x512, etc.)

- Filter > Other > Offset

You should insert values that are half of the width/height of your image. If your image is 512x512, use 256 for horizontal and vertical.

This moves the seams at the edges to the middle. Now we can see the seams and clean them up.

You can get rid of the seams by copy/pasting good parts of the image over the seams, or by using the Clone Stamp tool.

- Select the Clone Stamp tool
- Alt-click a seamless area you want to clone
- Left-click over the seams

If there are brightness differences, you can try the burn/darken tools to fix.

## Notes

* Original source for equalization - https://tolas.wordpress.com/2009/05/26/tutorial-how-to-equalize-textures-in-photoshop/
* Original source for seamless textures - http://www.designbash.com/photoshop/photoshop-offset-filter-making-seamless-textures/
