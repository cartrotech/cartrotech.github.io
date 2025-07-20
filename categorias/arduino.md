---
layout: default
title: Arduino
permalink: /categorias/arduino/
---

<div class="blog-container">

    <h1>Articles de Arduino</h1>

    {% assign arduino_posts = site.posts | where: "categories", "arduino" | sort: "date" %}
    {% for post in arduino_posts %}
    <article class="articulo">
        <p><a href="{{ post.url }}">{{ post.title }}</a></p>
    </article>
    {% endfor %}
</div>
