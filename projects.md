layout: default
title: Projects
permalink: /projects/
---

# Projects

Below are Featured projects you curate, followed by an auto‑listed set of your public repositories (excluding forks/archived). To feature repos, edit `_data/featured.yml`.

{% assign featured = site.data.featured | default: empty %}
{% assign repos = site.github.public_repositories %}

{% if featured and featured.size > 0 %}
## ⭐ Featured
<div class="grid">
  {% for item in featured %}
    {% assign nwo = item.repo %}
    {% assign repo_name = nwo | split: '/' | last %}
    {% assign gh = repos | where: 'name', repo_name | first %}
    <div class="card">
      <h3>
        <a href="{{ gh.html_url | default: ('https://github.com/' | append: nwo) }}">{{ item.title | default: (gh.name | default: repo_name) }}</a>
      </h3>
      {% if item.tags %}<p class="muted">{{ item.tags | join: ' · ' }}</p>{% elsif gh.language %}<p class="muted">{{ gh.language }}</p>{% endif %}
      {% if item.blurb %}<p>{{ item.blurb }}</p>{% elsif gh.description %}<p>{{ gh.description }}</p>{% endif %}
      <p class="muted">
        {% if gh.stargazers_count %}⭐ {{ gh.stargazers_count }} ·{% endif %}
        {% if gh.pushed_at %} Updated {{ gh.pushed_at | date: "%b %Y" }}{% endif %}
      </p>
      {% if item.homepage or gh.homepage %}
        <p><a href="{{ item.homepage | default: gh.homepage }}">Live</a></p>
      {% endif %}
    </div>
  {% endfor %}
</div>
{% endif %}

## All Repositories
<div class="grid">
  {% comment %} Build a comma-wrapped list of featured names to skip {% endcomment %}
  {% capture featured_names %}{% for i in featured %},{% assign n = i.repo | split:'/' | last %}{{ n }}{% endfor %},{% endcapture %}

  {% assign list = repos
    | where_exp: 'r', 'r.fork == false'
    | where_exp: 'r', 'r.archived == false'
    | sort: 'stargazers_count' | reverse %}

  {% for r in list %}
    {% assign token = ',' | append: r.name | append: ',' %}
    {% if featured_names contains token %}
      {% continue %}
    {% endif %}
    <div class="card">
      <h3><a href="{{ r.html_url }}">{{ r.name }}</a></h3>
      {% if r.language %}<p class="muted">{{ r.language }}</p>{% endif %}
      {% if r.description %}<p>{{ r.description }}</p>{% endif %}
      <p class="muted">⭐ {{ r.stargazers_count }} · Updated {{ r.pushed_at | date: "%b %Y" }}</p>
      {% if r.homepage %}<p><a href="{{ r.homepage }}">Live</a></p>{% endif %}
    </div>
  {% endfor %}
</div>

<p class="muted">Tip: add a <code>portfolio</code> topic to repos you want to highlight, then filter on that topic here if you prefer.</p>
