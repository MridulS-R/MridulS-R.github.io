---
layout: default
title: Tags
permalink: /tags/
---

# Tags

{% if site.tags and site.tags.size > 0 %}
<p class="muted">Browse posts by tag.</p>

<ul class="tag-cloud">
  {% assign sorted_tags = site.tags | sort %}
  {% for tag in sorted_tags %}
    {% assign name = tag[0] %}
    {% assign posts = tag[1] %}
    <li><a class="tag" href="#{{ name }}">#{{ name }}</a> <span class="muted">({{ posts | size }})</span></li>
  {% endfor %}
  </ul>

{% for tag in sorted_tags %}
  {% assign name = tag[0] %}
  {% assign posts = tag[1] %}
  <h2 id="{{ name }}">#{{ name }}</h2>
  <ul>
    {% for post in posts %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        <span class="muted">— {{ post.date | date: "%b %d, %Y" }}</span>
      </li>
    {% endfor %}
  </ul>
{% endfor %}
{% else %}
<p class="muted">No tags yet. Add tags to posts with <code>tags: [example]</code> in front matter.</p>
{% endif %}

