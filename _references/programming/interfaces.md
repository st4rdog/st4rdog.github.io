---
# BASICS
id       : rInterfaces
title    : "Interfaces"
date     : 2015-11-02
subtitle : "How to use Interfaces when making your game."
author   : aStardog

# OPTIONS - REFERENCE
isAvailable    : true
type           : programming
img            : ""
rel-references : ""

# OPTIONS - GENERAL
isHidden : false
---

<div id="paper"></div>

<script type="text/javascript">
var graph = new joint.dia.Graph();

var paper = new joint.dia.Paper({
    el: $('#paper'),
    width: 800,
    height: 120,
    gridSize: 1,
    model: graph
});

var uml = joint.shapes.uml;

var classes = {

    weapon: new uml.Interface({
        position: { x:0, y:2 },
        size: { width: 180, height: 100 },
        name: 'IWeapon',
        attributes: ['string variableName'],
        methods: ['void Attack()']
    }),

    damagedealer: new uml.Interface({
        position: { x:200, y:2 },
        size: { width: 180, height: 100 },
        name: 'IDamageDealer',
		methods: ['void DealDamage(IDamageable damageable, int amount)']
    }),
	
	equippable: new uml.Interface({
        position: { x:400, y:2 },
        size: { width: 180, height: 100 },
        name: 'IEquippable',
		methods: ['void Equip()', 'void Unequip()']
    })

};

_.each(classes, function(c) { graph.addCell(c); });

//var relations = [
//    new uml.Generalization({ source: { id: classes.man.id }, target: { id: classes.weapon.id }})
//];

_.each(relations, function(r) { graph.addCell(r); });
</script>

Interfaces are like a buffet of behaviours. You can pick and choose what behaviours you need.

They become useful when they are implemented by a Class. That means the Class inherits from the Interface.

## When to Use?

When you require similar behaviour from unrelated Classes.

## Examples

Sword, Dagger, ThrowingDagger and Shield
Inheritance can break down when your hierachy becomes too deep. In Unity, there's rarely a reason for inheritance to go beyond a few levels deep.

Imagine you have Sword, Dagger, ThrowingDagger and Shield Classes.

You decide to make Sword/Dagger/ThrowingDagger Inherit from Weapon so they can use its Attack() function. You also make Shield Inherit from Armor.

ThrowingDagger is a ranged weapon, which attacks in a different way to the Attack() in the Weapon Class, so you introduce Melee and Ranged Classes which override the Weapon's Attack().

### Problem

Later, you decide that Shields can also attack (shield bash), and can also be thrown.

Now you're stuck, because you can only Inherit from one Class. Do you make Shield inherit from Melee or Ranged? Then it would no longer be Armor...

### Solution

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

## Notes

* ...
* This could lead to duplicate code. For example, if every weapon/armour is equipped in the same way. The solution is to just do a GetComponent call to an Equip script.
* Interfaces vs Inheritance Help
  * http://forum.unity3d.com/threads/interfaces-vs-inheritance-help.373237/