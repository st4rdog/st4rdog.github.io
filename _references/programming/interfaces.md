---
# BASICS
refid    : rInterfaces
title    : "Interface"
date     : 2015-11-02
subtitle : "How to use Interfaces when making your game."
author   : aStardog

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%

# OPTIONS - REFERENCE
isAvailable    : false
type           : programming
rel-tutorials  : 
rel-references : [rClass, rCommunication]

# OPTIONS - GENERAL
isPublic     : true
showComments : true
---
<iframe src="https://docs.google.com/presentation/d/1g-nW1nz5bGKhykcRBzm30TooPrVVaY0iSohtO3UWVUc/embed?start=true&loop=true&delayms=1000" frameborder="0" width="820" height="490" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>

**Interfaces** are like a **buffet of behaviours**. You can pick and choose what behaviours you need.

They become useful when they are implemented by a Class. Each class will implement the interface in a unique way.

* TOC
{:toc}

## When to Use?

* When unrelated classes require similar functionality, but different implementations.
  * See example of Sword/Shield below.
  * If implementations are the same/shared, use a regular or abstract class.
* When you are already inheriting from a class, but need more behaviour.

## How they work

Interfaces have no implementation. They are a contract/template that an implementing class must match.

{% highlight csharp %}
public interface IDamageable
{
	void ApplyDamage(float amount);
}
{% endhighlight %}

This interface says that any class that uses it must have an ApplyDamage function that takes a variable of type float.

{% highlight csharp %}
public class TestClass : MonoBehaviour, IDamageable
{
	public float _currentHealth = 100;

	// Implementation of IDamageable
	public void ApplyDamage(float amount)
	{
		_currentHealth -= amount;
	}
}
{% endhighlight %}

TestClass implements the IDamageable interface. If you do not implement every function/property specified in the interface, you will get a compile error.

## Examples

### 1. Sword, Dagger, ThrowingDagger and Shield

Inheritance can break down when your hierachy becomes too deep. In Unity, there's rarely a reason for inheritance to go beyond a few levels deep.

Imagine you have Sword, Dagger, ThrowingDagger and Shield Classes.

You decide to make Sword/Dagger/ThrowingDagger Inherit from Weapon so they can use its Attack() function. You also make Shield Inherit from Armor.

ThrowingDagger is a ranged weapon, which attacks in a different way to the Attack() in the Weapon Class, so you introduce Melee and Ranged Classes which override the Weapon's Attack().

#### Problem

Later, you decide that Shields can also attack (shield bash), and can also be thrown.

Now you're stuck, because you can only Inherit from one Class. Do you make Shield inherit from Melee or Ranged? Then it would no longer be Armor...

#### Solution

One solution is to use Interfaces. It will allow unrelated Classes to have the same behaviours.

Note these Interfaces:

* IWeapon
* IArmor
* IThrowable
* IDamageDealer
* IEquippable
* IDancer

Notice that DancingShieldDaggerOfDoom is using all of the Interfaces, so it can behave like a weapon, a shield, a throwable, a damagedealer and a dancer, yet is not related to any other Class. Although not related to anything, it could still be added to a List of IEquippables, for example, alongside unrelated Classes.

Notice that Shield can now Attack() and Throw(), etc.

Notice that Sword/Dagger/ThrowingDagger still inherit from Weapon. It's Weapon that uses the Interfaces. Only ThrowingDagger implements the IThrowable Interface.

Here's what some of the Classes might look like:

<script src="https://gist.github.com/st4rdog/6dcfa011b0c86c1762a5.js"></script>

<script src="https://gist.github.com/st4rdog/18c18cb50131b0b49416.js"></script>

<script src="https://gist.github.com/st4rdog/b9b234078693273a98ae.js"></script>

### 2. Damageable objects

Interfaces can be used to "tag" classes as Damageable. This is an alternative to using a Damageable Component.

{% highlight csharp %}
public interface IDamageable
{
	void ApplyDamage(float amount);
}
{% endhighlight %}

You can check GameObjects for an interface using GetComponent like so:

{% highlight csharp %}
IDamageable damageable = GetComponent<IDamageable>();

if (damageable != null)
{
	// This GameObject has a script that implements IDamageable
	damageable.ApplyDamage(100);
}
{% endhighlight %}

TODO: Check answer - http://answers.unity3d.com/questions/60357/getcomponent-and-interfaces.html
Check if can get Component from interface
Check if Unity 5 works with just GetComponent<IInterface>();

## Notes

* Unity components can handle most situations that would normally require an interface.
* Interfaces will not show up in the inspector.
  * The solution is third-party inspector assets.
* Can lead to duplicate code. For example, if every weapon/armour is equipped in the same way.
  * The solution is to encapsulate the functionality into a regular C-Sharp class, or to an attached component, or inherit from a base class that contains the functionality.
* Interfaces vs Inheritance Help
  * http://forum.unity3d.com/threads/interfaces-vs-inheritance-help.373237/
* http://stackoverflow.com/questions/10914802/why-i-should-go-for-interfaces-in-c-sharp-when-i-can-implement-the-methods-direc
* http://forum.unity3d.com/threads/code-organization-inheritance-components-based-interfaces-requesting-opinions.304556/
* https://forum.unity.com/threads/component-based-weapon-system.204999/
* [WHY did I AVOID interfaces!? Discuss cool things u can do with them here.](https://forum.unity.com/threads/why-did-i-avoid-interfaces-discuss-cool-things-u-can-do-with-them-here.342776/)