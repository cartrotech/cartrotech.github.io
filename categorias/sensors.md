---
layout: default
title: Sensors
permalink: /categorias/sensors/
---

<div class="blog-container">
    <h1>Articles de Sensors de Arduino</h1>

    {% assign sensors_posts = site.posts | where: "categories", "sensors" | sort: "date" %}
    {% for post in sensors_posts %}
        <article class="articulo">
            <p><a href="{{ post.url }}">{{ post.title }}</a></p>
        </article>
    {% endfor %}
</div> 