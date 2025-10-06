---
layout: default
title: Blog
permalink: /blog/
---

# Blog

{% if site.posts and site.posts.size > 0 %}
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <span class="muted">— {{ post.date | date: "%b %d, %Y" }}</span>
      {%- if post.tags and post.tags.size > 0 -%}
        <span>
          {%- for tag in post.tags -%}
            <a class="tag" href="{{ '/tags/' | append: tag | slugify | append: '/' | relative_url }}">#{{ tag }}</a>
          {%- endfor -%}
        </span>
      {%- endif -%}
      {% if post.excerpt %}<div class="muted">{{ post.excerpt | strip_html }}</div>{% endif %}
    </li>
  {% endfor %}
  </ul>
{% else %}
<p class="muted">No posts yet. Create posts in the <code>_posts</code> folder.</p>
{% endif %}
