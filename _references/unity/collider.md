---
# BASICS
refid    : rCollider
title    : "Collider"
date     : 2015-11-02
subtitle : "How to use Colliders to allow GameObjects to bump into each other?"
author   : aStardog

# IMAGES
bg-img-path  : "001.png"
bg-img-scale : 150%

# OPTIONS - REFERENCE
isAvailable    : true
type           : unity
rel-tutorials  : 
rel-references : [rCharacterController, rComponent, rGameObject, rRigidbody]

# OPTIONS - GENERAL
isPublic : true
---
A **{{ page.title }}** is a <a href="{{ site.url }}{{ site.url-references-unity }}component">Component</a> that attaches to a <a href="{{ site.url }}{{ site.url-references-unity }}gameobject">GameObject</a>. It adds the ability to collide/interact with other colliders.

If there is no Collider component on a GameObject, other GameObjects will pass through it as if it doesn't exist, like a ghost.

* TOC
{:toc}

## Notes

* A <a href="{{ site.url }}{{ site.url-references-unity }}charactercontroller">CharacterController</a> looks like a Collider, but doesn't function in exactly the same way. Do not treat it like a regular collider.