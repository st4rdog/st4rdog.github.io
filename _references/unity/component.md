---
# BASICS
id       : rComponent
title    : "Component"
date     : 2015-11-02
subtitle : "How to use Components when making your game."
author   : aStardog

# IMAGES
bg-img-path  : "001.png"
bg-img-scale : 150%

# OPTIONS - REFERENCE
isAvailable    : true
type           : unity
rel-tutorials  : 
rel-references : [rCommunication, rClass, rGameObject]

# OPTIONS - GENERAL
isHidden : false
---
Components attach to <a href="{{ site.url }}{{ site.url-references-unity }}gameobject">GameObjects</a>. They are building blocks that add functionality to a GameObject.

They are an Instance of a <a href="{{ site.url }}{{ site.url-references-programming }}class">Class</a> that exists in the world.

* TOC
{:toc}

## Examples

### Physics Object

**Rigidbody** is a Component that allows the physics engine to take control of your GameObject.

**Sphere Collider** is a Component that allows your GameObject to bump into things, so it won't fall through the floor.

By adding both these components to a GameObject, it will create a realistic ball that will roll with physics.