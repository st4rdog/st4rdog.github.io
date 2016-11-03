---
# BASICS
refid    : rProperty
title    : "Property"
date     : 2015-11-02
subtitle : "How to use properties when making classes in Unity."
author   : aStardog

# IMAGES
bg-img-path  : "001.png"
bg-img-scale : 150%

# OPTIONS - REFERENCE
isAvailable    : true
type           : programming
rel-tutorials  : 
rel-references : [rClass]

# OPTIONS - GENERAL
isPublic     : true
showComments : true
---
<a href="https://msdn.microsoft.com/en-us/library/x9fsa0sw.aspx" class="external">**Properties**</a> are used to change a variable without accessing it directly. They also allow you to execute code before or after a variable is changed

Think of it as a gateway that you must go through to access a variable.

* TOC
{:toc}

## Why should I use Properties?

* To prevent a member variable from being changed directly.
* To error check before assigning a value to the member variable.

## When should I use Properties?

* When an outside class needs to change a variable.

## Examples

### Error checking

Properties can help us to stop member variables being set to the wrong value. In this example, <code>_name</code> should not be empty, and <code>_age</code> should not be less than 1. 

{% highlight csharp %}
public class Human : MonoBehaviour {

	public string _name;
	public int _age;
	
	void Start()
	{
		// These errors will not be picked up
		_name = "";
		_age = -20.
	}

}
{% endhighlight %}

We've made the variables private, so no outside class has access. They can instead use the new properties that we've added.

{% highlight csharp %}
public class Human : MonoBehaviour {

	private string _name;
	private int _age;
	
	void Start()
	{
		// These errors will not be picked up
		Name = "";
		Age = -20.
	}
	
	public string Name
	{
		get { return _name; }
		set { _name = value; }
	}
	
	public int Age
	{
		get { return _age; }
		set { _age = value; }
	}

}
{% endhighlight %}

Now, when a class sets <code>Age = 5</code>, the Age property will run the code inside <code>set</code>.

When a class sets <code>int number = Age</code>, the Age roperty will run the code inside <code>get</code>.

To add error checking, we must modify what happens when the properties are <code>set</code>.

{% highlight csharp %}
public class Human : MonoBehaviour {

	private string _name;
	private int _age;
	
	// When the game starts
	void Start()
	{
		// These errors will be picked up, so member variables will not be set to the wrong values.
		Name = "";
		Age = -20.
	}
	
	public string Name
	{
		get { return _name; }
		set
		{
			// If the value that we are trying to assign to _name is empty
			if ( value == "")
			{
				Debug.Log("Error: Name cannot be empty!");
			}
			else
			{
				// Apply value to member variable
				_name = value;
			}
		}
	}
	
	public int Age
	{
		get { return _age; }
		set
		{
			// If the value that we are trying to assign to _age is less than 1
			if ( value < 1)
			{
				Debug.Log("Error: Age cannot be less than 1!");
			}
			else
			{
				// Apply value to member variable
				_age = value;
			}
		}
	}

}
{% endhighlight %}

## Notes

* <a href="https://unity3d.com/learn/tutorials/topics/scripting/properties" class="external">Official Unity scripting tutorial</a>