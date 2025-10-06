---
layout: default
title: Blog
permalink: /blog/
---

# Blog

{% if site.posts and site.posts.size > 0 %}
<div class="grid">
  {% for post in site.posts %}
    <div class="card">
      <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
      <p class="muted">{{ post.date | date: "%b %d, %Y" }}</p>
      {% assign blurb = post.description | default: post.excerpt %}
      {% if blurb %}<p>{{ blurb | strip_html | truncate: 200 }}</p>{% endif %}
      {%- if post.tags and post.tags.size > 0 -%}
        <div class="meta">
          {%- for tag in post.tags -%}
            <a class="chip" href="{{ '/tags/' | append: tag | slugify | append: '/' | relative_url }}">#{{ tag }}</a>
          {%- endfor -%}
        </div>
      {%- endif -%}
    </div>
  {% endfor %}
</div>
{% else %}
<p class="muted">No posts yet. Create posts in the <code>_posts</code> folder.</p>
{% endif %}
