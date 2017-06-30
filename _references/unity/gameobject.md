---
# BASICS
refid    : rGameObject
title    : "GameObject"
date     : 2015-11-02
subtitle : "How to use GameObjects when making your Unity game."
author   : aStardog

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%

# OPTIONS - REFERENCE
isAvailable    : true
type           : unity
rel-tutorials  : 
rel-references : [rComponent, rScene, rInstantiate, rTransform]

# OPTIONS - GENERAL
isPublic : true
---
<a href="https://docs.unity3d.com/Manual/class-GameObject.html" class="external">GameObjects</a> are the objects that exist in a <a href="{{ site.url }}{{ site.url-references-unity }}scene">Scene</a>. <a href="{{ site.url }}{{ site.url-references-unity }}component">Components</a> are attached to add functionality/behaviour.

* TOC
{:toc}

## FAQ

* **What's the difference between a GameObject and a Prefab?**
  * Prefabs are assets that exist on your hard disk. When <a href="{{ site.url }}{{ site.url-references-unity }}instantiate">Instantiated</a>, they exist as GameObjects in your Scene.

## Notes

* Every selectable object in a Scene is a GameObject.
* Every GameObject has a <a href="{{ site.url }}{{ site.url-references-unity }}transform">Transform Component</a> attached by default. This serves to give it position/rotation/scale in the world.