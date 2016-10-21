---
# BASICS
refid    : tWASDMovement
title    : "WASD Movement"
date     : 2015-11-02
author   : aStardog

subtitle       : "How to make do basic WASD movement!"
subtitle-short : "How to make do basic WASD movement!"

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%

# OPTIONS - TUTORIAL
isAvailable    : false
type           : system
rel-tutorials  : 
rel-references : [rClass, rInput]

# OPTIONS - GENERAL
isPublic : true
---
**WASD movement** in Unity is very simple. The only complexity is fixing diagonal speed, so let's start.

* TOC
{:toc}

## Intro

We have to take the user's <a href="{{ site.url }}{{ site.url-references-unity }}input">Input</a> (usually a number between -1 and 1) and add it to the GameObject's current Position.

This will give us movement.

## Making input update the position

* Get Horizontal/Vertical <a href="{{ site.url }}{{ site.url-references-unity }}input">Input</a> values.
* Add to the Transform's position.

{% highlight csharp %}
void Update()
{
	float horizontal = Input.GetAxis("Horizontal");
	float vertical = Input.GetAxis("Vertical");

	Vector3 forward = transform.forward * vertical * speed * Time.deltaTime;
	Vector3 right = transform.right * horizontal * speed * Time.deltaTime;

	cc.Move(forward + right);
}
{% endhighlight %}

## Problem #1 - Relative forward

...

## Problem #2 - Collisions

If we simply add the input to the Transform components Position, the GameObject will go through walls. It's the same as if you were moving it inside the editor with the XYZ gizmo handles.

To fix this, we need to use a CharacterController component. Its Move() function will handle the complex collisions for us.

## Problem #3 - Diagonal movement is too fast

...

## Final code

<script src="https://gist.github.com/st4rdog/4ed0cb0bca5785f9e15d.js"></script>