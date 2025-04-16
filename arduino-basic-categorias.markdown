---
layout: page
title: Arduino Bàsic
permalink: /arduino-basic-categorias/
---

Esta página recopila todos los tutoriales y proyectos básicos de Arduino. Aquí encontrarás recursos para comenzar tu viaje en el mundo de la electrónica y la programación.

{% assign posts = site.posts | where_exp: "post", "post.categories contains 'arduino' and post.categories contains 'basic'" %}

{% if posts.size > 0 %}
  <ul class="post-list">
    {% for post in posts %}
      <li>
        <span class="post-meta">{{ post.date | date: "%d/%m/%Y" }}</span>
        <h3>
          <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
        </h3>
        {% if post.description %}
          <p>{{ post.description }}</p>
        {% endif %}
      </li>
    {% endfor %}
  </ul>
{% else %}
  <p>No hay posts disponibles con estas categorías.</p>
{% endif %} 