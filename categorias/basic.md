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
            <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
            <div class="fecha">
                Publicat el {{ post.date | date: "%-d de %B, %Y" }}
            </div>
            {% if post.excerpt %}
                <p class="resumen">{{ post.excerpt }}</p>
            {% endif %}
            <a href="{{ post.url }}" class="leer-mas">Llegir més →</a>
            <hr>
        </article>
        {% endfor %}
</div>
