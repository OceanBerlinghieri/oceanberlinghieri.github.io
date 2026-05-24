---
layout: page
title: Blog
permalink: /blog/
---

<h1>Last posts</h1>

<div class="posts-grid">

{% for post in site.posts limit 9 %}
<a href="{{ post.url }}">
<article class="post-card">

    <img src="{{ post.cover }}" alt="{{ post.title }}">

    <h2>{{ post.title }}</h2>

    <p>{{ post.excerpt }}</p>
</article>
</a>

{% endfor %}
</div>

<br>

<h1>Post categories</h1>

{% assign categories = site.posts | map: "categories" | uniq %}

{% for category in categories %}
<a href="/blog/{{ category }}/">
    {{ category }}
</a>
{% endfor %}


