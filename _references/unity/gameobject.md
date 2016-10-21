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
rel-references : [rComponent, rScene]

# OPTIONS - GENERAL
isPublic : true
---
Every <a href="{{ site.url }}{{ site.url-references-unity }}scene">Scene</a> contains a list of <a href="http://docs.unity3d.com/ScriptReference/GameObject.html" class="external">GameObjects</a>. <a href="{{ site.url }}{{ site.url-references-unity }}component">Components</a> are attached to add functionality/behaviour.

* TOC
{:toc}

## Notes

* All GameObjects come with a Transform Component. This gives a GameObject position/rotation/scale in the world.