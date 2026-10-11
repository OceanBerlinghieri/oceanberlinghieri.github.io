---
layout: page
title: Notas al margen
permalink: /notas_al_margen/
---

<h1>Reseñas recientes</h1>

<div class="posts-grid">

{% assign notas_al_margen_posts = site.posts | where_exp: "post", "post.categories contains 'notas_al_margen'" %}
{% for post in notas_al_margen_posts limit: 9 %}
<a href="{{ post.url }}">
<article class="post-card">

    <img src="{{ post.cover }}" alt="{{ post.title }}">

    <h2>{{ post.title }}</h2>

    <p>{{ post.excerpt }}</p>
</article>
</a>
{% endfor %}

</div>