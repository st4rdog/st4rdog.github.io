---
# BASICS
refid    : rSoftware
title    : "Useful Software"
date     : 2015-11-02
subtitle : "A list of software that will help you program."
author   : aStardog

# IMAGES
bg-img-path  : "001.jpg"
bg-img-scale : 250%

# OPTIONS - REFERENCE
isAvailable    : false
type           : programming
rel-tutorials  : 
rel-references : 

# OPTIONS - GENERAL
isPublic     : true
showComments : true
---
Here is a list of software that will help you program.

* TOC
{:toc}

<ul>
{% for i in site.data.software %}
	{% if i.types contains "programming" %}
		<li><a href="{{ i.homepage }}">{{ i.title }}</a>{% if i.description %} - {{ i.description }}{% endif %}</li>
	{% endif %}
{% endfor %}
</ul>