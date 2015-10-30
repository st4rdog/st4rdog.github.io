---
name: Stardog
id: aStardog
favourite-movie: Scarface
is-gamer: yes
is-tv-watcher: false
---

{{ page.name }} is the owner of the website.

{% if page.favourite-movie %}His favourite movie is {{ page.favourite-movie }}.{% endif %}

{% if page.is-gamer %}He also plays video games.{% endif %}

{% if page.is-tv-watcher %}He also enjoys watching TV.{% endif %}
