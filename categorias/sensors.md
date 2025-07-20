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