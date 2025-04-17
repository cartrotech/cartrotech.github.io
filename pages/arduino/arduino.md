---
layout: page
title: Arduino
permalink: /pages/arduino/arduino/
---

Aquesta pàgina recopila tots els tutorials i projectes de Arduino. Aquí trobaràs recursos per a començar el teu viatge en el món de l'electrònica i la programació.

{% assign posts = site.posts | where_exp: "post", "post.categories contains 'arduino'" %}

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
  <p>No hi ha posts disponibles amb aquestes categories.</p>
{% endif %} 