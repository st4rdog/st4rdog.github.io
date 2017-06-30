---
# BASICS
refid    : rCharacterController
title    : "CharacterController"
date     : 2015-11-02
subtitle : "How to use a CharacterController to make sure the Player can't walk through walls!"
author   : aStardog

# IMAGES
bg-img-path  : "001.png"
bg-img-scale : 150%

# OPTIONS - REFERENCE
isAvailable    : true
type           : unity
rel-tutorials  : 
rel-references : [rComponent, rCollider]

# OPTIONS - GENERAL
isPublic : true
---
A **{{ page.title }}** allows you to move <a href="{{ site.url }}{{ site.url-references-unity }}gameobject">GameObjects</a> manually while allowing them to collide with the environment.

It makes sure your GameObject does not fall through the floor or walk through walls.

* TOC
{:toc}

## Examples

...

## Notes

* A CharacterController looks like a <a href="{{ site.url }}{{ site.url-references-unity }}collider">Collider</a>, but doesn't function in exactly the same way. Do not treat it like a regular collider.