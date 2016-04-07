---
# BASICS
id       : tHealthBar
title    : "Health Bar"
date     : 2015-11-02
author   : aStardog

subtitle       : "How to make a health bar!"
subtitle-short : "How to make a health bar!"

# IMAGES
bg-img-path  : "001.png"
bg-img-scale : 180%

# OPTIONS - TUTORIAL
isAvailable    : true
type           : system
rel-tutorials  : [tHealth]
rel-references : [rClass, rCommunication]

# OPTIONS - GENERAL
isHidden : false
---
<div class="img-box">
	<div class="img-box-bg">
		<img src="{{ site.baseurl }}{{ site.url-imgs }}{{ page.url }}001.png" alt="Health bars" />
		<div class="caption">A range of health bar sliders we will be creating in Unity</div>
	</div>
</div>

* TOC
{:toc}

## Outline

**Health bars** in Unity can be creating using a UI Slider component. You can use this in a 2D or 3D user interface, or have it "in world" above a character's head.

It needs to be linked to our <a href="{{ site.baseurl }}{{ site.url-tutorials-system }}health" title="Unity Health Script">Health script</a> in order to change its value.

## Notes

* This UI system only exists in Unity 4.6 and higher