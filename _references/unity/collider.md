---
# BASICS
refid    : rCollider
title    : "Collider"
date     : 2015-11-02
subtitle : "How to use Colliders to allow GameObjects to bump into each other?"
author   : aStardog

# IMAGES
bg-img-path  : "001.png"
bg-img-scale : 150%
icon-fa-id   : f46b

# OPTIONS - REFERENCE
isAvailable    : true
type           : unity
rel-tutorials  : 
rel-references : [rCharacterController, rComponent, rGameObject, rRigidbody]
complexity     : 5

# OPTIONS - GENERAL
isPublic : true
---
A **{{ page.title }}** is a <a href="{{ site.url }}{{ site.url-references-unity }}component">Component</a> that attaches to a <a href="{{ site.url }}{{ site.url-references-unity }}gameobject">GameObject</a>. It adds the ability to collide/interact with other colliders.

<div class="anim-container animRB" style="height: 240px">

	<div class="progress-container">
		<div class="bar-wrapper">
			<div class="bar"></div>
		</div>
	</div>
	
	<div class="ballView"></div>
	
	<div class="box-container gameobject ballGO">
		<div class="title">Ball</div>
		<div class="box-container component c-sc">
			<div class="title">SphereCollider</div>
		</div>
		
		<div class="box-container component c-rb">
			<div class="title">RigidBody</div>
		</div>
	</div>

</div>

<script>
function animRB() {

	let progressBar = document.querySelector('.animRB .bar');

	let tl = anime.timeline({loop: true, autoplay: true, easing: 'easeInOutQuart', duration: 1000, update: anim => {progressBar.style.width = `${anim.progress}%`} /*, update: anim => {controlSeek.value = anim.progress}*/ });

	// Setup
	// TODO: Cube - https://codepen.io/desandro/pen/KRWjzm
	anime.set('.animRB .ballView', {opacity: 0, translateX: 600, width: 60, height: 60, scale: 0, borderRadius: '50%', borderWidth: '0px', borderStyle: 'solid', borderColor: ['rgba(0, 0, 0, 0)'], background: ['radial-gradient(circle at 30% 25%, white 1px, aqua 3%, darkblue 60%, aqua 100%)'], position: 'absolute'});
	anime.set('.animRB .ballGO', {opacity: 0, translateX: 250, translateY: 0, width: 250, scale: 0, paddingBottom: 25});
	anime.set('.animRB .c-sc', {opacity: 0, translateX: -250, width: 200, height: 40, scale: 0, marginBottom: 20, position: 'relative'});
	anime.set('.animRB .c-rb', {opacity: 0, translateX: -250, width: 200, height: 40, scale: 0, position: 'relative'});
	
	tl.add({targets: '.animRB .ballGO', delay: 1000, opacity: 1, scale: 1});
	tl.add({targets: '.animRB .ballView', opacity: 1, scale: 1}, '-=1000');
	
	tl.add({targets: '.animRB .c-sc', opacity: 1, scale: 1});
	tl.add({targets: '.animRB .c-sc', translateX: 25});
	tl.add({targets: '.animRB .ballView', duration: 100, borderColor: ['rgba(0, 230, 75, 1)'], borderWidth: '3px'}, '-=500');
	
	tl.add({targets: '.animRB .c-rb', opacity: 1, scale: 1});
	tl.add({targets: '.animRB .c-rb', translateX: 25});
	
	tl.add({targets: '.animRB .ballView', translateY: 100, easing: 'easeOutBounce'}, '-=400');
	
	tl.add({targets: '.animRB .ballView', delay: 2000, opacity: 1});
	
	// End
	tl.add({targets: '.animRB', scale: 0});
}
animRB();
</script>

If there is no Collider component on a GameObject, other GameObjects will pass through it as if it doesn't exist, like a ghost.

* TOC
{:toc}

## Notes

* A <a href="{{ site.url }}{{ site.url-references-unity }}charactercontroller">CharacterController</a> looks like a Collider, but doesn't function in exactly the same way. Do not treat it like a regular collider.
* [OnMouseDown() + Child Colliders issue solved](https://forum.unity3d.com/threads/onmousedown-child-colliders-issue-solved.29228/)
  * The parent rigidbody is the only one that gets any calls when a child collider is clicked on. (As far as I know). If you want the child to register its own calls, remove it from the hierarchy or give it its own rigidbody. 