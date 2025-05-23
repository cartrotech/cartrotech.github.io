---
layout: default
title: Display
---

<div class="blog-container">
    <h1>Articles de Display de Arduino</h1>

    {% for post in site.posts %}
        {% if post.categories contains "display" or post.categories contains "displays" %}
        <article class="articulo">
            <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
            <div class="fecha">
                Publicat el {{ post.date | date: "%-d de %B, %Y" }}
            </div>
            {% if post.excerpt %}
                <p class="resumen">{{ post.excerpt }}</p>
            {% endif %}
            <a href="{{ post.url }}" class="leer-mas">Llegir més →</a>
        </article>
        {% endif %}
    {% endfor %}
</div> 