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
