---
# BASICS
refid    : rEvent
title    : "Event"
date     : 2015-11-02
subtitle : "How to use Events when making your game."
author   : aStardog

# IMAGES
bg-img-path  : "001.png"
bg-img-scale : 150%

# OPTIONS - REFERENCE
isAvailable    : true
type           : programming
rel-tutorials  : 
rel-references : [rClass, rCommunication, rFindingAccessing, rUnityEvent]

# OPTIONS - GENERAL
isPublic     : true
showComments : true
---
**Events** are notifications that are sent to **subscribers** whenever something interesting happens.

They are one of the ways to communicate and send data between classes.

* TOC
{:toc}

## Intro

Think of an event as a signal that is broadcast. Interested parties (subscribers) can pick up the signal.

The event itself has no knowledge of the subscribers, and doesn't care. It simply sends the event. Subsribers register to receive the event, so they can act upon it.

## When to use Events in Unity?

* To decouple code.
* To send data to other scripts, without having any knowlede of the other script.
* When you want to run a single function than runs multiple other functions at once.

## Examples

### Light switch - C# Event

We can use events to notify subscribers of when a light switch is turned on and off.

{% highlight csharp %}
public class LightSwitch : MonoBehaviour
{
	// Delegate
	public delegate void EventHandler(); // A delegate can be thought of as a template. Subscribing methods must match this template.
	
	// Events
	public event EventHandler TurnedOn;
	public event EventHandler TurnedOff;

	void TurnOn()
	{
		if (TurnedOn != null)
		{
			TurnedOn();
		}
	}
	
	void TurnOff()
	{
		if (TurnedOff != null)
		{
			TurnedOff();
		}
	}
}
{% endhighlight %}

* A delegate can be thought of as a template. Subscribing methods must match this template.
* "EventHandler" delegate can be named anything you want.
* We create two events named TurnedOn and TurnedOff.
* Before firing the events, we have to check that subscribers exist, otherwise we will get an error.

{% highlight csharp %}
public class Light : MonoBehaviour
{
	[Header("References")]
	public Light light;
	public LightSwitch switchReference;
	
	void Awake()
	{
		// Get the light component on this GameObject
		light = GetComponent<Light>();
	
		// Subscribe to events from LightSwitch
		switchReference.TurnedOn += OnTurnedOn;
		switchReference.TurnedOff += OnTurnedOff;
	}

	void OnTurnedOn()
	{
		light.enabled = true;
	}
	
	void OnTurnedOff()
	{
		light.enabled = false;
	}
}
{% endhighlight %}

### Light Switch - UnityEvent

{% highlight csharp %}
using UnityEngine.Events;

public class LightSwitch : MonoBehaviour
{
	[Header("Events")]
	public UnityEvent TurnedOn;
	public UnityEvent TurnedOff;

	void TurnOn()
	{
		TurnedOn.Invoke();
	}
	
	void TurnOff()
	{
		TurnedOff.Invoke();
	}
}
{% endhighlight %}

{% highlight csharp %}
public class Light : MonoBehaviour
{
	[Header("References")]
	public Light light;
	public LightSwitch switchReference;
	
	void Awake()
	{
		// Get the light component on this GameObject
		light = GetComponent<Light>();
	
		// Subscribe to events from LightSwitch
		switchReference.TurnedOn().AddListener(OnTurnedOn);
		switchReference.TurnedOff().AddListener(OnTurnedOff);
	}

	void OnTurnedOn()
	{
		light.enabled = true;
	}
	
	void OnTurnedOff()
	{
		light.enabled = false;
	}
}
{% endhighlight %}

## UnityEvents vs C# Events

* UnityEvents with basic types (int, float, bool, etc) will show in the the Inspector. They don't require code to hook up.

## Events vs calling method directly

http://stackoverflow.com/questions/2660675/raising-events-vs-direct-method-calls-differences

Event raise = "If anyone is listening and cares, this thing just happened."

Method call = "Do this specific thing"

## Notes

* See Unity Events
* https://msdn.microsoft.com/en-gb/library/aa645739(v=vs.71).aspx
* https://www.youtube.com/watch?v=ju6mK6-e3Oo (UnityEvents Tutorial by GRFON guy https://www.assembla.com/spaces/grfon/wiki/Developer_Docs (new Apr 2017 link - https://app.assembla.com/spaces/grfon/wiki/Developer_Docs)
* https://forum.unity3d.com/threads/unityevent-where-have-you-been-all-my-life.321103/