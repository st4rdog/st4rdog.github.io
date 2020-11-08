---
# BASICS
refid    : rComponent
title    : "Component"
date     : 2015-11-02
subtitle : "How to use Components to add behaviour/functionality to GameObjects in Unity!"
author   : aStardog

# IMAGES
bg-img-path  : "001.png"
bg-img-scale : 150%
icon-fa-id   : f1b3

# OPTIONS - REFERENCE
isAvailable    : true
type           : unity
rel-tutorials  : 
rel-references : [rCamera, rCharacterController, rClass, rCollider, rCommunication, rGameObject, rInstantiate, rTransform]
complexity     : 1

# OPTIONS - GENERAL
isPublic : true
---
<!--
<div class="google-slides-wrapper">
	<iframe class="google-slides-iframe" src="https://docs.google.com/presentation/d/1j7F0cOOk8qabxrE2L6o8YXRK7oXBoJtlsIP3FJAff8A/embed?start=true&loop=true&delayms=1000" frameborder="0" width="820" height="490" allowfullscreen="true" mozallowfullscreen="true" webkitallowfullscreen="true"></iframe>
	<div class="border"></div>
	<div class="toolbar"><span>---</span>&lt;<span>---</span>PLAY<span>---</span>&gt;<span>---</span></div>
</div>
-->

Components attach to <a href="{{ site.url }}{{ site.url-references-unity }}gameobject">GameObjects</a> to give them functionality/behaviour.

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
	
	/*
	// https://codepen.io/juliangarnier/pen/RRKpgq
	// https://css-tricks.com/styling-cross-browser-compatible-range-inputs-css | https://www.cssportal.com/style-input-range/
	var controlSeek = document.querySelector('.anim-container .seek');
	var controlPlay = document.querySelector('.anim-container .play');
	var controlPause = document.querySelector('.anim-container .pause');
	var controlRestart = document.querySelector('.anim-container .restart');
	
	controlSeek.addEventListener('input', () => {
		tl.seek(tl.duration * (controlSeek.value / 100));
	});

	controlSeek.addEventListener('input', () => {
		tl.pause();
		controlPlay.innerHTML = 'Play';
	});
	
	controlPlay.addEventListener('click', () => {
		
		if (controlPlay.innerHTML == 'Play')
		{
			tl.play();
			controlPlay.innerHTML = 'Pause';
		}
		else
		{
			tl.pause();
			controlPlay.innerHTML = 'Play';
		}
	});
	
	controlRestart.addEventListener('click', () => {
		tl.restart();
		controlPlay.innerHTML = 'Pause';
	});
	*/
	
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

A component is an <a href="{{ site.url }}{{ site.url-references-unity }}instantiate">Instance</a> of a <a href="{{ site.url }}{{ site.url-references-programming }}class">Class</a> that exists in the Scene.

Custom components can be created to build any functionality you require in your game.

* TOC
{:toc}

## Examples

### Create a custom component

Custom components are created by coding a Class, and then making it inherit from MonoBehaviour. This allows you to click-drag it onto any GameObject or <a href="{{ site.url }}{{ site.url-references-unity }}prefab">Prefab</a>, and gives the class access to MonoBehaviours' features.

{% highlight csharp %}
public class Player : MonoBehaviour {
	
	[Header("Settings")]
	public string _name; // This will show in the Inspector when dragged onto a GameObject.
	
	void Start()
	{
		Debug.Log("This Start function only exists in MonoBehaviour!");
	}
	
	void Update()
	{
		Debug.Log("This Update function only exists in MonoBehaviour!");
	}

}
{% endhighlight %}

### Getting a component on the current GameObject

...

### Building a physics object from scratch

**Rigidbody** is a Unity Component that allows the physics engine to take control of your GameObject.

**Sphere Collider** is a Unity Component that allows your GameObject to bump into things, so it won't fall through the floor.

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
	anime.set('.animRB .ballView', {opacity: 0, translateX: 600, width: 100, height: 100, scale: 0, borderRadius: '50%', borderWidth: '0px', borderStyle: 'solid', borderColor: ['rgba(0, 0, 0, 0)'], background: ['radial-gradient(circle at 40% 20%, white 1px, aqua 3%, darkblue 60%, aqua 100%)'], position: 'absolute'});
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

By adding both these components to a GameObject, it will create a realistic ball that will roll with physics.

### Building a dog

Components allow you to build objects from modular pieces, so, to make a dog, you wouldn't necessarily have a Component named "Dog".

Instead, we build it out of Components that add behaviour, and attach them to the GameObject that represents the dog.

<div class="anim-container anim2" style="height: 240px">

	<div class="progress-container">
		<div class="bar-wrapper">
			<div class="bar"></div>
		</div>
	</div>
	
	<div class="box-container gameobject dog">
		
	</div>
	
	<div class="box-container component c-bark">
		<div class="title">Bark</div>
		<div class="group -method">
			<div class="item method">Bark()</div>
		</div>
	</div>
	
	<div class="box-container component c-jump">
		<div class="title">Jump</div>
		<div class="group -method">
			<div class="item method">Jump()</div>
		</div>
	</div>
	
	<div class="box-container component c-microchip">
		<div class="title">Microchip</div>
		<div class="group -field">
			<div class="item field string">ownerName = "Bob Smith"</div>
			<div class="item field int">ownerHouseNumber = 100</div>
			<div class="item field string">ownerAddress = "Beverly Hills"</div>
			<div class="item field string">ownerZipCode = "90210"</div>
		</div>
	</div>
	
</div>

<script>
function anim2() {

	let progressBar = document.querySelector('.anim2 .bar');

	let tl = anime.timeline({loop: true, autoplay: true, easing: 'easeInOutQuart', duration: 1000, update: anim2 => {progressBar.style.width = `${anim2.progress}%`} /*, update: anim => {controlSeek.value = anim.progress}*/ });

	// Setup
	anime.set('.anim2 .dog', {opacity: 0, translateX: 0, width: 250, scale: 0});
	anime.set('.anim2 .c-bark', {opacity: 0, translateX: 0, width: 230, scale: 0});
	anime.set('.anim2 .c-jump', {opacity: 0, translateX: 270, width: 230, scale: 0});
	anime.set('.anim2 .c-microchip', {opacity: 0, translateX: 560, width: 230, scale: 0});
	
	tl.add({targets: '.anim2 .c-bark', delay: 1000, opacity: 1, scale: 1});
	
	
	tl.add({targets: '.anim2 .c-jump', delay: 1000, opacity: 1, scale: 1});
	
	
	tl.add({targets: '.anim2 .c-microchip', delay: 1000, opacity: 1, scale: 1});
	
	tl.add({targets: '.anim2 .c-microchip', delay: 5000, opacity: 1, scale: 1});
	
	// End
	tl.add({targets: '.anim2', scale: 0});
}
anim2();
</script>

**Bark** is a custom Component that contains a <code>Bark()</code> function.

{% highlight csharp %}
public class Bark : MonoBehaviour {
	
	void Bark()
	{
		Debug.Log("Barked!");
	}

}
{% endhighlight %}

**Jump** is a custom Component that contains a <code>Jump()</code> function.

{% highlight csharp %}
public class Jump : MonoBehaviour {
	
	void Jump()
	{
		Debug.Log("Jumped!");
	}

}
{% endhighlight %}

**Microchip** is a custom Component that contains microchip data about the dog's owners.

{% highlight csharp %}
public class Microchip : MonoBehaviour {
	
	[Header("Info")]
	public string _ownerName = "Bob Smith";
	public int _ownerHouseNumber = 100;
	public string _ownerAddress = "Beverly Hills";
	public string _ownerZipCode = "90210";
	
}
{% endhighlight %}

### Building a Player character

**<a href="{{ site.url }}{{ site.url-references-unity }}charactercontroller">CharacterController</a>** is a Unity Component that contains a useful <code>Move()</code> function which allows us to collide with objects while moving.

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

**Player** is a custom Component that simply 'tags' a GameObject as the player. It's used instead of Unity's <a href="https://docs.unity3d.com/Manual/Tags.html" class="external">tag</a> system.

{% highlight csharp %}
public class Player : MonoBehaviour { }
{% endhighlight %}

**MoveHorizontal** is a custom Component that stores Input values and puts them into the CharacterController's <code>Move()</code> function.

{% highlight csharp %}
public class MoveHorizontal : MonoBehaviour {
	
	[Header("References")];
	private CharacterController _cc;
	
	void Awake()
	{
		// Store CharacterController component
		_cc = GetComponent<CharacterController>();
	}
	
	void Update()
	{
		// Create a float to store input value from A/D keys, left/right arrow keys, and left analog stick.
		float h = Input.GetAxis("Horizontal");
		
		// Create a Vector3 to store our direction. h moves us on the X axis, and v moves us on the Y axis.
		Vector3 moveDirection = new Vector3(h, 0f, 0f);
		
		// Apply movement
		_cc.Move(moveDirection);
	}

}
{% endhighlight %}

**CharacterInfo** lets us give our player a name, etc. It can also attach to any other character that needs a name.

{% highlight csharp %}
public class CharacterInfo : MonoBehaviour {
	
	[Header("Info")];
	public string _firstName;
	public string _secondName;
	public int _age;

}
{% endhighlight %}

## Notes

* Public member variables will be initialized automatically by the editor.
  * `public List<int> myList;` will work.
  * `public List<int> myList = new List<int>()` is still recommended.