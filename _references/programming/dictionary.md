---
# BASICS
refid    : rDictionary
title    : "Dictionary"
date     : 2015-11-02
subtitle : "How to use dictionaries when making games in Unity."
author   : aStardog

# IMAGES
bg-img-path  : "001.png"
bg-img-scale : 150%
icon-fa-id   : f02d

# OPTIONS - REFERENCE
isAvailable    : false
type           : programming
rel-tutorials  : 
rel-references : [rClass, rArray, rList]

# OPTIONS - GENERAL
isPublic     : true
showComments : true
---
Dictionaries allow you to find items quickly. They are a collection of values/items that can be accessed via a key. 

In a regular word dictionary, the key is the word, and the value is the description of the word.

* Aardvark (Key)
  * A strange looking mammal with a big nose. (Value)

* TOC
{:toc}

## When to Use?

* ...

## Examples

### Word Dictionary

Here's how to set up a basic dictionary of words and their meaning.
{% highlight csharp linenos %}
public Dictionary<string, string> _wordDictionary = new Dictionary<string, string>();

void Awake()
{
	_wordDictionary.Add("Aardvark", "A strange looking mammal with a big nose.");
	_wordDictionary.Add("Dog", "A mammal with an acute sense of smell.");
	
	Debug.Log(_wordDictionary["Aardvark"]);
}
{% endhighlight %}

* Create a new empty dictionary called _wordDictionary. The key/value will both be pieces of text, so we use string.
* Add new items to the dictionary (Aardvark and Dog).
* Log the value contained under Aardvark.
  * We access the key via square brackets e.g. <code class="inline">dictionaryName[key]</code>.

### Inventory Items
Here is a basic item class that holds some useful data and methods. It has a constructor we can use when creating a new item.

{% highlight csharp linenos %}
public class Item {

	// Fields
	public string _name = "Default Item Name";
	public int _weight = 10;
	public int _attackPower = 25;
	
	// Constructor
	public Item(string name, int weight, int attackPower)
	{
		_name = name;
		_weight = weight;
		_attackPower = attackPower;
	}

}
{% endhighlight %}

Here is a dictionary holding multiple items.

{% highlight csharp linenos %}
public Dictionary<string, Item> _inventory = new Dictionary<string, Item>();

void Awake()
{
	_inventory.Add("Bad Sword", new Item("Short Sword", 5, 12));
	_inventory.Add("Awesome Sword", new Item("Long Sword", 10, 150)
	
	Debug.Log(_inventory["Awesome Sword"]._name);
}
{% endhighlight %}

## Notes

* ...