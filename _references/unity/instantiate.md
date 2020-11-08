---
# BASICS
refid    : rInstantiate
title    : "Instantiate"
date     : 2015-11-02
subtitle : "How to create/copy/duplicate an object in Unity?"
author   : aStardog

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%
icon-fa-id   : f24d

# OPTIONS - REFERENCE
isAvailable    : true
type           : unity
rel-tutorials  : 
rel-references : [rGameObject, rPrefab, rComponent]
complexity     : 1

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
		// Instantiates the prefab into the scene as a GameObject
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
		// Instantiates a GameObject into the scene, but stores the instance in a member variable.
		_instanceOfPrefab = Instantiate(_prefab);
		
		// Now we can do anything with the reference to the instance
		_instanceOfPrefab.name = "Bob";
		_instanceOfPrefab.transform.position = new Vector3(1f, 10f, 1f);
	}

}
{% endhighlight %}

Same as above, but stores the instance in a local variable instead of a member variable.

{% highlight csharp %}
public class TestScript : MonoBehaviour {

	public GameObject _prefab;

	void Start()
	{
		GameObject instanceOfPrefab = Instantiate(_prefab);
		
		instanceOfPrefab.name = "Bob";
		instanceOfPrefab.transform.position = new Vector3(1f, 10f, 1f);
	}

}
{% endhighlight %}

### Instantiate with a reference to a Component on the GameObject

Instantiate was updated by Unity to understand what type the object is you are trying to instantiate.

In Visual Studio, you can hover over Instantiate with the mouse cursor and a tooltip will show you the Type it's trying to return.

{% highlight csharp %}
public class TestScript : MonoBehaviour {

	// We dragged a prefab in here that contained a HealthScript component
	public HealthScript _healthComponent;

	void Start()
	{
		// Instantiates the full prefab as a GameObject in the scene, then returns the HealthScript component that is on it
		_healthComponent = Instantiate(_healthComponent);
		
		// We can access the HealthScript immediately, without requiring GetComponent.
		_healthComponent.Heal(50);
		
		// Note: To destroy the GameObject, remember to use the gameObject property
		Destroy(_healthComponent.gameObject);
		
		// Destroys only the HealthScript Component on the GameObject, leaving GameObject in the scene
		Destroy(_healthComponent);
	}

}
{% endhighlight %}

Before this feature, a [hard or soft Cast](https://stackoverflow.com/questions/2483/casting-newtype-vs-object-as-newtype) was required. See the following example:

{% highlight csharp %}
public class TestScript : MonoBehaviour {

	public GameObject _prefab;

	void Start()
	{
		// Soft cast - will return null if it doesn't work. You can check for null and continue.
		_prefab = Instantiate(_prefab) as GameObject;
		
		// Hard cast - will create an exception if it doesn't work.
		_prefab = (GameObject)Instantiate(_prefab);
	}

}
{% endhighlight %}

## Notes

* Instantiate was updated at some point to return the Type of the object you are trying to instantiate, so no casting is required. If using an older version, it is recommened to soft cast to the type you desire, otherwise it will return you an Object.
* <a href="https://docs.unity3d.com/ScriptReference/Object.Instantiate.html" class="external">Official Unity Scripting API - Instantiate</a>