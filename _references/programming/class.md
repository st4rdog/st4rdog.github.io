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

# OPTIONS - REFERENCE
isAvailable    : true
type           : programming
rel-tutorials  : 
rel-references : [rInheritance, rCommunication, rComponent, rFindingAccessing, rGameObject, rInterfaces, rField, rMethod, rProperty, rVariable]

# OPTIONS - GENERAL
isPublic     : true
showComments : true
---
<iframe src="https://docs.google.com/presentation/d/e/2PACX-1vSmztXUVKCXtNAHk3h_QDe75xGHszpB-ABi8iF3lAwiQllTb7UOJBawCGxMXS5cbxj86lwaHTl2IQGF/embed?start=true&loop=true&delayms=1000" frameborder="0" width="820" height="490" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>

A **Class** is a group of related **Variables** and **Functions**. It allows your game to know what something is and what it can do.

* **Variable**
  * Holds data of a certain Type (text, number, true/false, other class, etc)
  * Examples: Age, Color, Weight

* **Function**
  * Executes an action. Makes something happen.
  * Examples: Jump(), Move()

Just like high school, mathematics class contains all the information about mathematics. Mathematics doesn't contain any information about history or art.

A **Class** can be added to a **GameObject** as a **Component**.

An **Instance** is a version/copy of a Class that exists "in the world". Cake is to recipe, as Instance is to Class.

* TOC
{:toc}

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

## Notes
* Classes should be a group of related things. In school, a history class does not teach mathematics. They focus on one topic.