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