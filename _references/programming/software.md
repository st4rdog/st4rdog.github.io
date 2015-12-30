---
# BASICS
id       : rSoftware
title    : "Useful Software"
date     : 2015-11-02
subtitle : "A list of software that will help you program."
author   : aStardog

# OPTIONS - REFERENCE
isAvailable    : true
type           : programming
img            : ""
rel-references : ""

# OPTIONS - GENERAL
isHidden : false
---
Here is a list of software that will help you program.

<ul>
{% for i in site.data.software %}
	{% if i.types contains "programming" %}
		<li><a href="{{ i.homepage }}">{{ i.title }}</a>{% if i.description %} - {{ i.description }}{% endif %}</li>
	{% endif %}
{% endfor %}
</ul>