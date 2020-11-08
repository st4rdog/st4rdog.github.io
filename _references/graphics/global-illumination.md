---
# BASICS
refid    : rGlobalIllumination
title    : "Global Illumination"
date     : 2017-06-08
subtitle : "What is Global Illumination in Unity?"
author   : aStardog

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%
icon-fa-id   : f6c4

# OPTIONS - REFERENCE
isAvailable    : true
type           : graphics
rel-tutorials  : 
rel-references : [rLighting, rLightmapping]

# OPTIONS - GENERAL
isPublic     : true
showComments : true
---
**{{ page.title }}** (GI) is a fancy name for a system that models indirect lighting - light that has bounced from one surface onto another.

<div style="display: flex; justify-content: space-around;">

	<div class="img-box -card">
		<img class="img" src="{{ site.baseurl }}{{ site.url-imgs }}{{ page.url }}gi_cube.gif" alt="No GI - Direct Light Only - Direct Light with GI" />
		<div class="caption">Light bouncing onto interior columns</div>
	</div>
	
	<div class="img-box -card">
		<img class="img" src="{{ site.baseurl }}{{ site.url-imgs }}{{ page.url }}gi_cube_interior.gif" alt="No GI - Direct Light Only - Direct Light with GI" />
		<div class="caption">Light bouncing through corridors</div>
	</div>

</div>

GI allows you to light a large area with just a single light source.

<div style="display: flex; justify-content: space-around;">

	<div class="img-box -card">
		<img class="img" src="{{ site.baseurl }}{{ site.url-imgs }}{{ page.url }}cube2_004.png" alt="GI from a single sunlight" />
		<div class="caption">GI from a directional light</div>
	</div>
	
	<div class="img-box -card">
		<img class="img" src="{{ site.baseurl }}{{ site.url-imgs }}{{ page.url }}cube1_004.png" alt="GI from a single point light" />
		<div class="caption">GI from a single point light</div>
	</div>

</div>


* TOC
{:toc}

## Notes

* ...
