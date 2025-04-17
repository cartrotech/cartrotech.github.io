---
layout: page
title: Arduino
permalink: /arduino-tutorials/
---

# Arduino

Explora els nostres articles organitzats per categories. Troba contingut relacionat amb els teus interessos i necessitats.

## Categories

### Arduino i Electrònica
- [Tots els articles d'Arduino](/pages/arduino/arduino)
- [Arduino bàsic](/pages/arduino/arduino-basic)
- [Sensors i Actuadors](/categories/sensors)
- [Projectes Electrònics](/categories/electronics)

### Disseny i Fabricació
- [Dissenyys en Cartró](/categories/cartro)
- [Patrons i Plantilles](/categories/patrons)
- [Tècniques de Fabricació](/categories/fabricacio)

### Educació STEAM
- [Activitats Educatives](/categories/educacio)
- [Recursos per a Docents](/categories/recursos-docents)
- [Experiments i Demostracions](/categories/experiments)

### Tutorials i Guies
- [Guies Pas a Pas](/categories/tutorials)
- [Consells i Trucs](/categories/consells)
- [Recursos d'Aprenentatge](/categories/recursos)

## Darrers Articles

{% for post in site.posts limit:5 %}
- [{{ post.title }}]({{ post.url }}) - {{ post.date | date: "%d/%m/%Y" }}
{% endfor %}

## Subscriu-te

No et perdis cap article! Subscriu-te al nostre [feed RSS](/feed.xml) o segueix-nos a les xarxes socials per estar al dia de les novetats. 