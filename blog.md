---
layout: page
title: Blog
permalink: /blog/
---

<h1>Last posts</h1>

<div class="posts-grid">

{% assign engineering_posts = site.posts | where_exp: "post", "post.categories contains 'engineering'" %}
{% for post in engineering_posts limit 9 %}
<a href="{{ post.url }}">
<article class="post-card">

    <img src="{{ post.cover }}" alt="{{ post.title }}">

    <h2>{{ post.title }}</h2>

    <p>{{ post.excerpt }}</p>
</article>
</a>

{% endfor %}
</div>



