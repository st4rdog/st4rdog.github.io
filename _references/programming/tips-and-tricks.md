---
# BASICS
refid    : rTipsTricksCode
title    : "Tips & Tricks (C#)"
date     : 2015-11-02
subtitle : "Helpful tips and tricks for C# using Unity."
author   : aStardog

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%
icon-fa-id   : f0d0

# OPTIONS - REFERENCE
isAvailable    : true
type           : programming
rel-tutorials  : 
rel-references : [rProperty, rTipsTricks]
complexity     : 1

# OPTIONS - GENERAL
isPublic : true
showComments : true
---
* TOC
{:toc}

## Basic Math - Add/subtract or increment/decrement assignment

{% highlight csharp %}
public int number = 10;

// Full (adds one to variable)
number = number + 1;

// Shortened
number += 1;

// Shortest
number++;
{% endhighlight %}

The shortened version also supports other math operations.

## String Interpolation

<a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/tokens/interpolated" class="external">String Interpolation</a> is an easier way to build strings out of multiple pieces.

{% highlight csharp %}
void Start()
{
	var name = "Mark";
	var age = 25;
	var day = "Tuesday";
	
	// Composite - hard to know what you are writing
	Debug.LogFormat("My name is {0}. I am {1}. Today is {2}.", name, age, day);
	
	// Concatenation - too much syntax
	Debug.Log("My name is " + name + ". I am " + age.ToString() + ". Today is " + day + ".");
	
	// Interpolation - easy to understand
	Debug.Log($"My name is {name}. I am {age}. Today is {day}.");
}

{% endhighlight %}

## Expression-bodied members

A <a href="https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members" class="external">C\#6 feature</a> that is syntactic sugar (designed to make things easier to read or express).

{% highlight csharp %}
// Long Methods
void Method()
{
	Debug.Log("Hello");
}

float MethodWithReturn()
{
	return 100f;
}

// Shortened Methods
void Method() => Debug.Log("Hello");
float MethodWithReturn() => 100f;
{% endhighlight %}

{% highlight csharp %}
// Long Property
public string Name
{
	get { return name; }
	set { name = value; }
} 

// Shortened Property
public string Name
{
	get => name;
	set => name = value;
} 
{% endhighlight %}

{% highlight csharp %}
// Long read-only Property
public string Name
{
	get { return name; }
}

// Shortened read-only Property
public string Name => name;
{% endhighlight %}

## Lambda expressions

Shorthand syntax for anonymous delegates - <a href="https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions" class="external">C# Programming Guide</a>.

{% highlight csharp %}
public Action<float> OnSomethingHappened;

void Start()
{
	// Long event subscription - requires creation of the DoWhenSomethingHappened method
	OnSomethingHappened += DoWhenSomethingHappened;
	
	// Shortened event subscription - anonymous function, written inline.
	OnSomethingHappened += f => Debug.Log(f);
	
	// Shortened event subscription - example of required syntax when there are no parameters, or two or more parameters.
	OnSomethingHappened += () => Debug.Log("Hello");
	OnSomethingHappened += (param1, param2) => Debug.Log($"{param1} {param2}");
}

// Long event handler method
void DoWhenSomethingHappened(float f)
{
    Debug.Log(f);
}
{% endhighlight %}

## var keyword

The <a href="https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables" class="external">var keyword</a> allows you to create variables without telling the compiler what type it is. The compiler will infer the type.

{% highlight csharp %}
// Long local variable declaration
List<LongTypeNameGoesHere> variableName = new List<LongTypeNameGoesHere>();

// Shortened local variable declaration
var variableName = new List<LongTypeNameGoesHere>();
{% endhighlight %}

{% highlight csharp %}
// Long foreach loop
foreach(GameObject go in GameObjectList)
{
    Debug.Log(go.name);
}

// Shortened foreach loop
foreach(var go in GameObjectList)
{
    Debug.Log(go.name);
}
{% endhighlight %}

## Inine out parameters

Since C&#35;7, you can inline an out parameter. No need to create a local variable.

{% highlight csharp %}
if (Physics.Raycast(ray, out var hitInfo, 1000f))
{
   Debug.Log(hitInfo.collider.name);
}
{% endhighlight %}

{% highlight csharp %}
if (TryGetComponent<Rigidbody>(out var rb))
{
    rb.AddForce...
}
{% endhighlight %}

## Value Tuples

<a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/value-tuples" class="external">Value Tuples</a> allow you to group values without having to create a Struct/Class.

Example without <a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/value-tuples#tuple-assignment-and-deconstruction" class="external">deconstruction</a>.
{% highlight csharp %}
(string Name, int Age, string Location) PersonData = ("Bob", 55, "USA");

Debug.Log($"{PersonData.Name}, {PersonData.Age}, {PersonData.Location}");
{% endhighlight %}

Example with deconstruction to reduce repetition
{% highlight csharp %}
(string Name, int Age, string Location) = ("Bob", 55, "USA");

Debug.Log($"{Name}, {Age}, {Location}");
{% endhighlight %}

Example using a list.
{% highlight csharp %}
public List<(int ID, GameObject Enemy)> Enemies;

// No deconstruction
foreach(var instance in Enemies)
{
	Debug.Log(instance.Enemy.name);
}

// Deconstructed
foreach(var (ID, Enemy) in Enemies)
{
	Debug.Log(Enemy.name);
}
{% endhighlight %}

## Multiple return types

You can effectively have multiple return types by using <a href="https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/value-tuples" class="external">Value Tuples</a>.

{% highlight csharp %}
public (bool Successful, int Value, GameObject Another) FunctionName()
{
    return (true, 25, GameObject.Find("Player"));
}
{% endhighlight %}

## Method Chaining

Method chaining can be achieved when a Method returns the instance of the Class it's inside.

{% highlight csharp %}
class Test
{
    public Test MethodOne { return this; }
    public Test MethodTwo { return this; }
    public Test MethodThree { return this; }
	
	void HowToUse()
	{
		MethodOne().MethodTwo().MethodThree();
	}
}

class AnotherClass
{
	var test = new Test() // Note: no semi-colon here.
		.MethodOne()
		.MethodTwo()
		.MethodThree();
}
{% endhighlight %}

They can be used to create [Fluent Interface API's](https://en.wikipedia.org/wiki/Fluent_interface).

There is an excellent [Finite State Machine](https://github.com/Real-Serious-Games/Fluent-State-Machine) and [Behaviour Tree](https://github.com/ashleydavis/Fluent-Behaviour-Tree) for Unity that do this. See the [associated article](http://www.what-could-possibly-go-wrong.com/fluent-behavior-trees-for-ai-and-game-logic/).

## Cast Interface to MonoBehaviour

When working with Interfaces that are implemented on MonoBehaviours, you will not be able to access the Component or GameObject the Interface is on.

To allow this, you must cast it.

{% highlight csharp %}
public class PlayerComponent : MonoBehaviour, IInteractor
{
	IInteractor _interactorInterface;

	void Awake()
	{
		_interactorInterface = this;

		var test = _interactorInterface as MonoBehaviour;

		// Prints "PlayerGameObject"
		Debug.Log($"GameObject name is {test.gameObject.name}");
		// Prints "PlayerComponent"
		Debug.Log($"Component type is {test.GetType()}");
	}
	
	// Also works the other way, from Component to Interface
	PlayerComponent _playerComponent;
	
	void Start()
	{
		_playerComponent = this;
		
		var test = _playerComponent as IInteractor;
		
		test.Interact();
	}
}
{% endhighlight %}

{% highlight csharp %}
public interface IWeapon
{
	void Fire();
}

public class WeaponComponent : MonoBehaviour, IWeapon
{
    void Fire() { Debug.Log("Firing!"); }
}

public class AttackSystem : MonoBehaviour
{
	// Assigned from another script, for example:
	// Example 1: attackSystem.CurrentlyEquipped = instanceOfPrefab.GetComponent<WeaponComponent>();
	// Example 2: attackSystem.CurrentlyEquipped = instanceOfPrefab.GetComponent<IWeapon>();
	IWeapon _currentlyEquippedWeapon;
	
	IWeapon CurrentlyEquipped { get => _currentlyEquippedWeapon; set => _currentlyEquippedWeapon = value; }
	
	void Update()
	{
		if (Input.GetMouseButtonDown(0))
		{
			_currentlyEquippedWeapon.Fire();
			
			// PROBLEM:
			// I want to print the name of the GameObject that has the WeaponComponent on it, but how?
			// _currentlyEquippedWeapon has no access to MonoBehaviour methods/properties, it can only access Fire().
			Debug.Log("?")
			
			// So we create a new variable and cast it to MonoBehaviour.
			var weaponBehaviour = _currentlyEquippedWeapon as MonoBehaviour;
			
			// It works because IWeapon is implemented on the WeaponComponent MonoBehaviour. Otherwise it will be null.
			if (weaponBehaviour != null)
			{
				Debug.Log($"{weaponBehaviour.gameObject.name} fired!")
			}
		}
	}
}
{% endhighlight %}

### Notes

- https://www.algorithm-archive.org