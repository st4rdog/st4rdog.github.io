---
# BASICS
id       : rInheritance
title    : "Inheritance"
date     : 2015-11-02
subtitle : "How to use inheritance when making your game."
author   : aStardog

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%

# OPTIONS - REFERENCE
isAvailable    : true
type           : programming
rel-tutorials  : 
rel-references : [rClass, rCommunication]

# OPTIONS - GENERAL
isHidden : false
---
Inheritance allows you to share information amongst child Classes. Just like a human baby can share attributes of its parents (hair colour, etc).

* TOC
{:toc}

## When to Use?

* When you don't want to repeat code.
* Inherit from a Class to gain access to the functionality you need.


* To create a different "type" of something.
  * Poodle is a type of Dog.
  * Pikachu is a type of Pokemon.

## Examples

### Dogs

All dogs can Bark(). So, when making a Poodle and a Labrador Class, you don't want to put the same Bark() function on both of them. That's code duplication.

One solution is to make a Dog Class with a Bark() Function. Then make the Poodle/Labrador inherit from Dog. They will both be able to call the Bark() function, because they now have access to the Dogs Class's public variables/functions.

If a Poodle needs to Bark() differently to other Dogs, you can mark Bark() as "virtual". This means Poodle can have its own Bark() function that overrides the one in in the Dog Class.

Unity Components give you another option. You could make a Barkable Class with a Bark() Function, then attach it to any GameObject that needs to Bark(). When it's time to Bark(), you use GetComponent [TODO: Link to Communication] to find Barkable and call Bark().

[TODO: NClass IMG]

## Problems

* You can only inherit from one Class.
* If you need functionality from many different classes, see Interfaces [TODO: Link to Interfaces].
  * Also see Components.
  * http://forum.unity3d.com/threads/multiple-inheritance-implementation-alternative.367802

## Notes

* When creating a Class inside Unity, it automatically inherits from MonoBehaviour.
  * This gives you access to all of MonoBehaviour's features and allows you to attach it as a Component.
* Unity Components give you another option. They can be used like a base Class.
* http://programmers.stackexchange.com/questions/134097/why-should-i-prefer-composition-over-inheritance