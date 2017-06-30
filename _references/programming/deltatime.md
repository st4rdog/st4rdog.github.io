---
# BASICS
refid    : rDeltaTime
title    : "DeltaTime"
date     : 2015-11-02
subtitle : "How to use deltaTime when making your game."
author   : aStardog

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%

# OPTIONS - REFERENCE
isAvailable    : true
type           : programming
rel-tutorials  : 
rel-references : [rProgrammingOptimisation]

# OPTIONS - GENERAL
isPublic     : true
showComments : true
---
<a href="http://docs.unity3d.com/ScriptReference/Time-deltaTime.html" class="external">**deltaTime**</a> is the time in seconds it took to complete the last frame.

<!--
<canvas class="emscripten" id="canvas" oncontextmenu="event.preventDefault()" height="480px" width="820px"></canvas>
<script type='text/javascript'>
  var Module = {
    TOTAL_MEMORY: 268435456,
    errorhandler: null,			// arguments: err, url, line. This function must return 'true' if the error is handled, otherwise 'false'
    compatibilitycheck: null,
    backgroundColor: "#F8F8F8",
    splashStyle: "Light",
    dataUrl: "{{ site.baseurl }}{{ site.url-media }}{{ page.url }}Release/DeltaTime.data",
    codeUrl: "{{ site.baseurl }}{{ site.url-media }}{{ page.url }}Release/DeltaTime.js",
    asmUrl: "{{ site.baseurl }}{{ site.url-media }}{{ page.url }}Release/DeltaTime.asm.js",
    memUrl: "{{ site.baseurl }}{{ site.url-media }}{{ page.url }}Release/DeltaTime.mem",
  };
</script>
-->

* **0.01666** if you are getting 60fps (1 divided by 60)
* **0.03333** if you are getting 30fps

Multiplying by deltaTime will make sure things happen in **units per second**, instead of **units per frame**.

If you do not multiply by deltaTime, you will get different values on different devices. On faster machines, objects will move faster and be further ahead of objects on slower machines.

* TOC
{:toc}

## When to Use?

Usually when you have code that needs to do something over time.

* Moving any object over time.
* Incrementing a number over time.

## Examples

### Moving an object along the X axis

{% highlight csharp %}
public Transform _cube;

void Update()
{
	// Move the cube 1 unit per frame along the X axis (to the right)
	_cube.Translate(1f, 0f, 0f);
}
{% endhighlight %}

If you have a frame-rate of 60, after 1 second, the cube will be at position (60, 0, 0).

If you have a frame-rate of 30, after 1 second, the cube will be at position (30, 0, 0).

Not good!

{% highlight csharp %}
public Transform _cube;

void Update()
{
    // Move the cube 1 unit per second along the X axis (to the right)
	_cube.Translate(1f * Time.deltaTime, 0f, 0f);
}
{% endhighlight %}

After 1 second, the cube will be at position (1, 0, 0), regardless of frame-rate. Everyone gets the same result.

Good!

## Notes

* http://docs.unity3d.com/ScriptReference/Time-deltaTime.html
* http://forum.unity3d.com/threads/the-truth-about-fixedupdate.231637/#post-2442966
* http://fabiensanglard.net/timer_and_framerate/index.php

<!--<script src="{{ site.baseurl }}{{ site.url-media }}{{ page.url }}Release/UnityLoader.js"></script>-->