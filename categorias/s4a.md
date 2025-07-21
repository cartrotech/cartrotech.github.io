---
layout: default
title: S4A
permalink: /categorias/s4a/
---

<div class="blog-container">

    <h1>Articles de Scratch for Arduino S4A</h1>

    {% assign s4a_posts = site.posts | where: "categories", "s4a" | where_exp: "post", "post.order != nil" | sort: "order" %}
    {% for post in s4a_posts %}
    <article class="articulo">
        <p><a href="{{ post.url }}">{{ post.title }}</a></p>
    </article>
    {% endfor %}
</div>
