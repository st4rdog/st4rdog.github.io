---
# BASICS
refid    : rClass
title    : "Class"
date     : 2015-11-02
subtitle : "How to use Classes when making your game."
author   : aStardog

# IMAGES
bg-img-thumb-path  : "001_thumb.png"
bg-img-thumb-scale : 100%
icon-fa-id         : f46d

# OPTIONS - REFERENCE
isAvailable    : true
type           : programming
rel-tutorials  : 
rel-references : [rInheritance, rCommunication, rComponent, rEvent, rFindingAccessing, rGameObject, rInterfaces, rField, rMethod, rProperty, rVariable]

# OPTIONS - GENERAL
isPublic     : true
showComments : true
---
A **Class** is a group of related **Variables** and **Functions**. It allows your game to know what something is and what it can do.

<div class="google-slides-wrapper">
	<iframe class="google-slides-iframe" src="https://docs.google.com/presentation/d/e/2PACX-1vSmztXUVKCXtNAHk3h_QDe75xGHszpB-ABi8iF3lAwiQllTb7UOJBawCGxMXS5cbxj86lwaHTl2IQGF/embed?start=true&loop=true&delayms=1000" frameborder="0" width="820" height="490" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
	<div class="border"></div>
	<div class="toolbar"><span>---</span>&lt;<span>---</span>PLAY<span>---</span>&gt;<span>---</span></div>
</div>

* TOC
{:toc}

## Summary

A **Class** is a group of related **Variables** and **Functions**, known as **Members**. It allows your game to know what something is and what it can do.

<div class="anim-container anim3" style="height: 240px">

	<div class="progress-container">
		<div class="bar-wrapper">
			<div class="bar"></div>
		</div>
	</div>
	
	<div class="box-container component c-player">
		<div class="title">Player</div>
	</div>
	
	<div class="box-container component c-cc">
		<div class="title">CharacterController</div>
		<div class="group -method">
			<div class="item method">Move()</div>
		</div>
	</div>
	
	<div class="box-container component c-move">
		<div class="title">MoveHorizontal</div>
		<div class="group -field">
			<div class="item field">
				<div class="el type">CharacterController</div>
				<div class="el name">cc</div>
			</div>
		</div>
		<div class="group -method">
			<div class="item method">Awake()</div>
			<div class="item method">Update()</div>
		</div>
	</div>
	
	<div class="box-container component c-info">
		<div class="title">CharacterInfo</div>
		<div class="group -field">
			<div class="item field string">
				<div class="el type">string</div>
				<div class="el name">firstName</div>
			</div>
			<div class="item field string">
				<div class="el type">string</div>
				<div class="el name">secondName</div>
			</div>
			<div class="item field int">
				<div class="el type">int</div>
				<div class="el name">age</div>
			</div>
		</div>
	</div>
	
</div>

<script>
function anim3() {

	let progressBar = document.querySelector('.anim3 .bar');

	let tl = anime.timeline({loop: true, autoplay: true, easing: 'easeInOutQuart', duration: 1000, update: anim => {progressBar.style.width = `${anim.progress}%`} /*, update: anim => {controlSeek.value = anim.progress}*/ });

	// Setup
	anime.set('.anim3 .c-player', {opacity: 0, translateX: 0, width: 230, scale: 0});
	anime.set('.anim3 .c-cc', {opacity: 0, translateY: 60, width: 230, scale: 0});
	anime.set('.anim3 .c-move', {opacity: 0, translateX: 270, width: 230, scale: 0});
	anime.set('.anim3 .c-info', {opacity: 0, translateX: 560, width: 230, scale: 0});
	
	tl.add({targets: '.anim3 .c-player', delay: 1000, opacity: 1, scale: 1});
	
	tl.add({targets: '.anim3 .c-cc', delay: 1000, opacity: 1, scale: 1});
	
	tl.add({targets: '.anim3 .c-move', delay: 1000, opacity: 1, scale: 1});
	
	tl.add({targets: '.anim3 .c-info', delay: 1000, opacity: 1, scale: 1});
	
	tl.add({targets: '.anim3 .c-info', delay: 4000, opacity: 1});
	
	// End
	tl.add({targets: '.anim3', scale: 0});

}
anim3();
</script>


* **Variable**
  * Holds data of a certain Type (text, number, true/false, other class, etc)
  * Examples: **Age**, **Color**, **Weight**

* **Function**
  * Executes an action. Makes something happen.
  * Examples: **Jump()**, **Move()**

Just like high school, mathematics class contains all the information about mathematics. Mathematics doesn't contain any information about history or art.

A **Class** can be added to a **GameObject** as a **Component**.

An **Object** (or **Instance**) is a version/copy of a Class that exists "in the world" (in memory). Think of a Class as the recipe, and the Object/Instance as the cake. Many Instances can be created from the same Class.

## Variable Basics

Variables can hold different types of data.

### Standard Types

{% highlight csharp %}
int    number;      // Holds a single whole number
float  decimalNum;  // Holds a single decimal number
string text;        // Holds text
bool   trueOrFalse; // Holds a true or false value
{% endhighlight %}

### Unity Types

{% highlight csharp %}
GameObject go;           // Holds a GameObject
Transform  t;            // Holds a GameObject's Transform component
Vector2    twoNumbers;   // Holds two numbers (x, y)
Vector3    threeNumbers; // Holds three numbers (x, y, z)
{% endhighlight %}

### Others

{% highlight csharp %}
GameObject[]                   array;      // Holds many GameObjects
List<Transform>                list;       // Holds many Transform components
Dictionary<string, GameObject> dictionary; // Holds many GameObjects found using a string ID
CustomClass                    myClass;    // Holds a custom class
{% endhighlight %}

### Access

Variables can be public or private (and more).

* **Public** means it is accessible from other Classes.
* **Private** means it is only accessible from inside its own Class.

## Function Basics

Functions make something happen when executed. They are sometimes called Methods.

### Standard

{% highlight csharp %}
void Jump()
{
    Debug.Log("Jumped");
}
{% endhighlight %}

### With a Parameter

{% highlight csharp %}
void Jump(int howHigh)
{
    Debug.Log("Jumped " + howHigh + " metres into the air");
}
{% endhighlight %}

### Returns a Type

{% highlight csharp %}
bool IsAlive()
{
    if (_currentHealth > 0)
    {
        return true;
    }
    else
    {
        return false;
    }
}

// Can be used like so:
void TestFunction()
{
    if (IsAlive())
    {
        // Alive
    }
    else
    {
        // Dead
    }
}
{% endhighlight %}

## Examples
* http://pastebin.com/cnSUVVac

## Class vs Unity Component

- Instantiating is different for both
  - Class - `ClassName varName = new ClassName();`
  - Component - `ClassName varName = gameObject.AddComponent<ClassName>();`, or click-drag the component onto the GameObject.

## Notes
* Classes should be a group of related things. In school, a history class does not teach mathematics. They focus on one topic.
* https://forum.unity.com/threads/component-based-weapon-system.204999/
* Self - Make differences between classes/structs clear
* http://www.tutorialsteacher.com/csharp/csharp-class
* http://www.tutorialsteacher.com/csharp/csharp-data-types
* [C# Programming Yellow Book by Rob Miles](https://static1.squarespace.com/static/5019271be4b0807297e8f404/t/5df9306ec60881645ea57ced/1576611956760/CSharp+Book+2019+Refresh.pdf)