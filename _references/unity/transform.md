---
# BASICS
refid    : rTransform
title    : "Transform"
date     : 2015-11-02
subtitle : "How to use the Transform component to Position, Rotate and Scale a GameObject!"
author   : aStardog

# IMAGES
bg-img-path  : "001.png"
bg-img-scale : 150%
icon-fa-id   : f065

# OPTIONS - REFERENCE
isAvailable    : true
type           : unity
rel-tutorials  : 
rel-references : [rComponent, rGameObject]
complexity     : 1

# OPTIONS - GENERAL
isPublic : true
---
The **Transform** <a href="{{ site.url }}{{ site.url-references-unity }}component">Component</a> determines the Position, Rotation, and Scale of each object in the scene. Every <a href="{{ site.url }}{{ site.url-references-unity }}gameobject">GameObject</a> has a Transform.

It contains useful functions such as Rotate, LookAt and Translate. And also useful variables such as *position*, *rotation* and *forward*.

* TOC
{:toc}

## Examples

### Shortcut variable

Because Transform is a common component, there is a shortcut <a href="{{ site.url }}{{ site.url-references-programming }}property">property</a> available to access it in any <a href="{{ site.url }}{{ site.url-references-unity }}monobehaviour">MonoBehaviour</a>.

This will save you having to use <a href="{{ site.url }}{{ site.url-references-unity }}component">GetComponent</a>.

Using the shortcut:

{% highlight csharp %}
public class Rotator : MonoBehaviour {

	void Update()
	{
		transform.Rotate(0, 1, 0); // Rotates the current GameObject
	}

}
{% endhighlight %}

Without using the shortcut:

{% highlight csharp %}
public class Rotator : MonoBehaviour {

	private Transform _transform;

	void Awake()
	{
		_transform = GetComponent<Transform>(); // Get the Transform component on the current GameObject, and store it in _transform
	}

	void Update()
	{
		_transform.Rotate(0, 1, 0); // Rotates the current GameObject
	}

}
{% endhighlight %}

## Notes

* ...