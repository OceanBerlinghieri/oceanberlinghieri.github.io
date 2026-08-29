---
layout: page
title: Imaginarium
permalink: /imaginarium/
---

<h1>Recent wanderings</h1>

<div class="posts-grid">

{% assign imaginarium_posts = site.posts | where_exp: "post", "post.categories contains 'imaginarium'" %}
{% for post in imaginarium_posts limit: 9 %}
<a href="{{ post.url }}">
<article class="post-card">

    <img src="{{ post.cover }}" alt="{{ post.title }}">

    <h2>{{ post.title }}</h2>

    <p>{{ post.excerpt }}</p>
</article>
</a>
{% endfor %}

</div>