---
# BASICS
refid    : rInstantiate
title    : "Instantiate"
date     : 2015-11-02
subtitle : "How to create instances of objects in Unity."
author   : aStardog

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%

# OPTIONS - REFERENCE
isAvailable    : true
type           : unity
rel-tutorials  : 
rel-references : [rGameObject, rPrefab, rComponent]

# OPTIONS - GENERAL
isPublic : true
---
**<a href="https://docs.unity3d.com/ScriptReference/Object.Instantiate.html" class="external">Instantiate</a>** creates/spawns/instantiates a copy/clone of an object.

* TOC
{:toc}

## Examples

### Instantiate a prefab when the game starts

The following code will create/spawn/instantiate an instance of a prefab you have referenced.

{% highlight csharp %}
public class TestScript : MonoBehaviour {

	public GameObject _prefab;

	void Start()
	{
		// Instantiates with default parameters
		Instantiate(_prefab);
		
		// Instantiates with custom position
		Instantiate(_prefab, new Vector3(10f, 20f, 30f));
		
		// Instantiates with custom position and rotation
		Instantiate(_prefab, new Vector3(10f, 20f, 30f), Quaternion.identity);
	}

}
{% endhighlight %}

### Instantiate with a reference to the instance

Sometimes you want to operate on an object immediately after you have instantiated it.

{% highlight csharp %}
public class TestScript : MonoBehaviour {

	public GameObject _prefab;
	public GameObject _instanceOfPrefab;

	void Start()
	{
		// Instantiates with default parameters, but stores the instance in a member variable. Note, it must be cast to GameObject using parenthesis.
		_instanceOfPrefab = (GameObject)Instantiate(_prefab);
		
		// Now we can do anything with the reference to the instance
		_instanceOfPrefab.name = "Bob";
		_instanceOfPrefab.transform.position = new Vector3(1f, 10f, 1f);
	}

}
{% endhighlight %}

Same as above, but stores the instance in a local variable.

{% highlight csharp %}
public class TestScript : MonoBehaviour {

	public GameObject _prefab;

	void Start()
	{
		GameObject instanceOfPrefab = (GameObject)Instantiate(_prefab);
		
		instanceOfPrefab.name = "Bob";
		instanceOfPrefab.transform.position = new Vector3(1f, 10f, 1f);
	}

}
{% endhighlight %}

## Notes

* <a href="https://docs.unity3d.com/ScriptReference/Object.Instantiate.html" class="external">Official Unity Scripting API - Instantiate</a>