---
# BASICS
refid    : rGameObject
title    : "GameObject"
date     : 2015-11-02
subtitle : "How to use GameObjects when making your Unity game."
author   : aStardog

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%
icon-fa-id   : f6d1

# OPTIONS - REFERENCE
isAvailable    : true
type           : unity
rel-tutorials  : 
rel-references : [rComponent, rScene, rInstantiate, rTransform]
complexity     : 1

# OPTIONS - GENERAL
isPublic : true
---
<a href="https://docs.unity3d.com/Manual/class-GameObject.html" class="external">GameObjects</a> are the objects that exist in a <a href="{{ site.url }}{{ site.url-references-unity }}scene">Scene</a>. <a href="{{ site.url }}{{ site.url-references-unity }}component">Components</a> are attached to add functionality/behaviour.

<div class="anim-container anim1" style="height: 300px">

	<!--
	<div class="controls-container">
		<input type="range" min="0" max="100" value="0" class="seek" style="z-index: 100">
		<button class="play">Pause</button>
		<button class="restart">Restart</button>
	</div>
	-->
	
	<div class="progress-container">
		<div class="bar-wrapper">
			<div class="bar"></div>
		</div>
	</div>

	<div class="box-container gameobject go1">
		<div class="title">GameObject</div>
		
		<div class="box-container component component1">
			<div class="title">Component</div>
		</div>
		
		<div class="box-container component component2">
			<div class="title">Component</div>
		</div>
		
		<div class="box-container component component3">
			<div class="title">Component</div>
		</div>
	</div>

	
	<div class="box-container gameobject go2">
		<div class="title">Pikachu</div>
	</div>
	
	<div class="box-container component component-pokemon">
		<div class="title">Pokemon</div>
	</div>
	
	<div class="box-container component component-abilities">
		<div class="title">Abilities</div>
	</div>
	
	<div class="box-container component component-stats">
		<div class="title">Stats</div>
	</div>
	
	
	
</div>

<script>
	let progressBar = document.querySelector('.anim1 .bar');

	let tl = anime.timeline({loop: true, autoplay: true, easing: 'easeInOutQuart', duration: 1000, update: anim => {progressBar.style.width = `${anim.progress}%`} /*, update: anim => {controlSeek.value = anim.progress}*/ });

	// Setup
	anime.set('.go1', {opacity: 0, width: 250, height: 40, scale: 0});
	anime.set('.component1', {opacity: 0, translateX: 270, height: 40, scale: 0, marginBottom: 20, marginTop: 5});
	anime.set('.component2', {opacity: 0, translateX: 270, height: 40, scale: 0, marginBottom: 20});
	anime.set('.component3', {opacity: 0, translateX: 270, height: 40, scale: 0});
	
	anime.set('.go2', {opacity: 0, width: 250, height: 40, translateX: 300});
	anime.set('.component-pokemon', {opacity: 0, translateX: 270, height: 40, marginBottom: 20, marginTop: 5});
	anime.set('.component-abilities', {opacity: 0, translateX: 270, height: 40, marginBottom: 20});
	anime.set('.component-stats', {opacity: 0, translateX: 270, height: 40});
	
	// Animation
	tl.add({targets: '.go1', delay: 1000, opacity: 1, scale: 1});

	tl.add({targets: '.component1', opacity: 1, scale: 1, begin: () => {
		document.querySelector(".component1").style.position = "relative";
		document.querySelector(".component2").style.position = "relative";
		document.querySelector(".component3").style.position = "relative";
		}});
	tl.add({targets: '.component1', translateX: 25});
	tl.add({targets: '.go1', height: 110}, '-=1000');
	
	tl.add({targets: '.component2', opacity: 1, scale: 1});
	tl.add({targets: '.component2', translateX: 25});
	
	tl.add({targets: '.go1', height: 170}, '-=1000');
	
	tl.add({targets: '.component3', opacity: 1, scale: 1});
	tl.add({targets: '.component3', translateX: 25});
	
	tl.add({targets: '.go1', height: 230}, '-=1000');
	
	// End
	tl.add({targets: '.gameobject', scale: 0});
	
</script>

* TOC
{:toc}

## FAQ

* **What's the difference between a GameObject and a Prefab?**
  * Prefabs are assets that exist on your hard disk. When <a href="{{ site.url }}{{ site.url-references-unity }}instantiate">Instantiated</a>, they exist as GameObjects in your Scene.

## Notes

* Every selectable object in a Scene is a GameObject.
* Every GameObject has a <a href="{{ site.url }}{{ site.url-references-unity }}transform">Transform Component</a> attached by default. This serves to give it position/rotation/scale in the world.