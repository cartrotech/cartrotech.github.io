---
layout: default
title: Bàsic
permalink: /categorias/basic/
---

<div class="blog-container">

    <h1>Articles de Arduino bàsic</h1>

    {% assign basic_posts = site.posts | where: "categories", "basic" | sort: "date" %}
        {% for post in basic_posts %}
        <article class="articulo">
            <p><a href="{{ post.url }}">{{ post.title }}</a></p>
        </article>
        {% endfor %}
</div>
