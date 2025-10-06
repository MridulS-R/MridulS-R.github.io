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
    <li><a class="tag" href="{{ '/tags/' | append: name | slugify | append: '/' | relative_url }}">#{{ name }}</a> <span class="muted">({{ posts | size }})</span></li>
  {% endfor %}
  </ul>

<hr />
<p class="muted">Direct links above navigate to per-tag pages.</p>
{% else %}
<p class="muted">No tags yet. Add tags to posts with <code>tags: [example]</code> in front matter.</p>
{% endif %}
