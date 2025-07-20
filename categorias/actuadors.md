---
layout: default
title: Actuadors
permalink: /categorias/actuadors/
---

<div class="blog-container">
    <h1>Articles de Actuadors de Arduino</h1>

    {% assign actuadors_posts = site.posts | where: "categories", "actuadors" | sort: "date" %}
    {% for post in actuadors_posts %}
        <article class="articulo">
            <p><a href="{{ post.url }}">{{ post.title }}</a></p>
        </article>
    {% endfor %}
</div>
