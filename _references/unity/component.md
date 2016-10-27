---
# BASICS
refid    : rComponent
title    : "Component"
date     : 2015-11-02
subtitle : "How to use Components to add behaviour/functionality to GameObjects!"
author   : aStardog

# IMAGES
bg-img-path  : "001.png"
bg-img-scale : 150%

# OPTIONS - REFERENCE
isAvailable    : true
type           : unity
rel-tutorials  : 
rel-references : [rCamera, rClass, rCollider, rCommunication, rGameObject, rInstantiate]

# OPTIONS - GENERAL
isPublic : true
---
Components attach to <a href="{{ site.url }}{{ site.url-references-unity }}gameobject">GameObjects</a> to give them functionality/behaviour.

A component is an <a href="{{ site.url }}{{ site.url-references-unity }}instantiate">Instance</a> of a <a href="{{ site.url }}{{ site.url-references-programming }}class">Class</a> that exists in the Scene.

Custom components can be created to build any functionality you require in your game.

* TOC
{:toc}

## Examples

### Create a custom component

Custom components are created by coding a Class, and then making it inherit from MonoBehaviour. This allows you to click-drag it onto any GameObject or <a href="{{ site.url }}{{ site.url-references-unity }}prefab">Prefab</a>, and gives the class access to MonoBehaviours' features.

{% highlight csharp %}
public class Player : MonoBehaviour {
	
	[Header("Settings")]
	public string _name; // This will show in the Inspector when dragged onto a GameObject.
	
	void Start()
	{
		Debug.Log("This Start function only exists in MonoBehaviour!");
	}
	
	void Update()
	{
		Debug.Log("This Update function only exists in MonoBehaviour!");
	}

}
{% endhighlight %}

### Building a physics object from scratch

**Rigidbody** is a Unity Component that allows the physics engine to take control of your GameObject.

**Sphere Collider** is a Unity Component that allows your GameObject to bump into things, so it won't fall through the floor.

By adding both these components to a GameObject, it will create a realistic ball that will roll with physics.

### Building a dog

Components allow you to build objects from modular pieces, so, to make a dog, you wouldn't necessarily have a Component named "Dog".

Instead, we build it out of Components that add behaviour, and attach them to the GameObject that represents the dog.

**Bark** is a custom Component that contains a <code>Bark()</code> function.

{% highlight csharp %}
public class Bark : MonoBehaviour {
	
	void Bark()
	{
		Debug.Log("Barked!");
	}

}
{% endhighlight %}

**Jump** is a custom Component that contains a <code>Jump()</code> function.

{% highlight csharp %}
public class Jump : MonoBehaviour {
	
	void Jump()
	{
		Debug.Log("Jumped!");
	}

}
{% endhighlight %}

**Microchip** is a custom Component that contains microchip data about the dog's owners.

{% highlight csharp %}
public class Microchip : MonoBehaviour {
	
	[Header("Info")]
	public string _ownerName = "Bob Smith";
	public int _ownerHouseNumber = 100;
	public string _ownerAddress = "Beverly Hills";
	public string _ownerZipCode = "90210";
	
}
{% endhighlight %}

### Building a Player character

**<a href="{{ site.url }}{{ site.url-references-unity }}charactercontroller">CharacterController</a>** is a Unity Component that contains a useful <code>Move()</code> function which allows us to collide with objects while moving.

**Move** is a custom Component that stores Input values and puts them into the CharacterController's <code>Move()</code> function.

{% highlight csharp %}
public class MoveHorizontal : MonoBehaviour {
	
	[Header("References")];
	private CharacterController _cc;
	
	void Awake()
	{
		// Store CharacterController component
		_cc = GetComponent<CharacterController>();
	}
	
	void Update()
	{
		// Create a float to store input value from A/D keys, left/right arrow keys, and left analog stick.
		float h = Input.GetAxis("Horizontal");
		
		// Create a Vector3 to store our direction. h moves us on the X axis, and v moves us on the Y axis.
		Vector3 moveDirection = new Vector3(h, 0f, 0f);
		
		// Apply movement
		_cc.Move(moveDirection);
	}

}
{% endhighlight %}

**CharacterInfo** lets us give our player a name, etc. It can also attach to any other character that needs a name.

{% highlight csharp %}
public class CharacterInfo : MonoBehaviour {
	
	[Header("Info")];
	public string _firstName;
	public string _secondName;
	public int _age;

}
{% endhighlight %}

## Notes

* ...