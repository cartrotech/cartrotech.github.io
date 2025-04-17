---
layout: page
title: Arduino
permalink: /arduino-tutorials/
---

# Arduino

Explora els nostres articles organitzats per categories. Troba contingut relacionat amb els teus interessos i necessitats.

- [Tots els articles d'Arduino](/pages/arduino/arduino)
- [Arduino bàsic](/pages/arduino/arduino-basic)
- [Sensors i Actuadors](#)
- [Projectes Electrònics](#)

## Darrers Articles

{% for post in site.posts limit:5 %}
- [{{ post.title }}]({{ post.url }}) - {{ post.date | date: "%d/%m/%Y" }}
{% endfor %}

## Subscriu-te

No et perdis cap article! Segueix-nos a les xarxes socials per estar al dia de les novetats. 