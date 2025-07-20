---
layout: default
title: Display
permalink: /categorias/display/
---

<div class="blog-container">
    <h1>Articles de Display de Arduino</h1>

    {% assign display_posts = site.posts | where: "categories", "display" | sort: "date" %}
    {% for post in display_posts %}
        <article class="articulo">
            <p><a href="{{ post.url }}">{{ post.title }}</a></p>
        </article>
    {% endfor %}
</div> 