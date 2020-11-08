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
icon-fa-id   : f21d

# OPTIONS - REFERENCE
isAvailable    : true
type           : unity
rel-tutorials  : 
rel-references : [rComponent, rCollider]
complexity     : 3

# OPTIONS - GENERAL
isPublic : true
---
A **{{ page.title }}** is a <a href="{{ site.url }}{{ site.url-references-unity }}component">Component</a> that allows you to move a <a href="{{ site.url }}{{ site.url-references-unity }}gameobject">GameObject</a> while allowing it to collide with the environment.

By using the CharacterController's `Move()` function, you can move a GameObject while making sure it does not fall through the floor or move through walls.

* TOC
{:toc}

## Notes

* A CharacterController looks like a <a href="{{ site.url }}{{ site.url-references-unity }}collider">Collider</a>, but doesn't function in exactly the same way. Do not treat it like a regular collider.