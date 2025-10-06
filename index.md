---
layout: default
title: "Mridul Shukla — Senior Software Engineer"
image: "https://svg-banners.vercel.app/api?type=glitch&text1=Hello%20World!&text2=Senior%20Software%20Engineer&width=1600&height=350"
---

<section class="hero center">
  <h1 class="title">👋 Hi, I’m MRIDUL SHUKLA</h1>
  <p class="subtitle">Senior Software Engineer · Rails/Backend · Java/Backend · Python/Django</p>
  <!-- CTA buttons removed to avoid duplicate Projects/Blog links with navbar -->
  <div class="badges">
  <img src="https://img.shields.io/badge/Ruby_on_Rails-%23CC0000.svg?logo=rubyonrails&logoColor=white&style=for-the-badge" alt="Rails"/>
  <img src="https://img.shields.io/badge/Ruby-CC342D?logo=ruby&logoColor=white&style=for-the-badge" alt="Ruby"/>
  <img src="https://img.shields.io/badge/PostgreSQL-316192?logo=postgresql&logoColor=white&style=for-the-badge" alt="Postgres"/>
  <img src="https://img.shields.io/badge/Elasticsearch-005571?logo=elasticsearch&logoColor=white&style=for-the-badge" alt="Elasticsearch"/>
  <img src="https://img.shields.io/badge/Sidekiq-CC0000?logo=ruby&logoColor=white&style=for-the-badge" alt="Sidekiq"/>
  <img src="https://img.shields.io/badge/AWS-232F3E?logo=amazon-aws&logoColor=white&style=for-the-badge" alt="AWS"/>
  <img src="https://img.shields.io/badge/Java-007396?logo=java&logoColor=white&style=for-the-badge" alt="Java"/>
  <img src="https://img.shields.io/badge/Spring-6DB33F?logo=spring&logoColor=white&style=for-the-badge" alt="Spring"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white&style=for-the-badge" alt="Docker"/>
  <img src="https://img.shields.io/badge/Redis-DC382D?logo=redis&logoColor=white&style=for-the-badge" alt="Redis"/>
  <img src="https://img.shields.io/badge/Node.js-339933?logo=node.js&logoColor=white&style=for-the-badge" alt="Node.js"/>
  <img src="https://img.shields.io/badge/Swift-FA7343?logo=swift&logoColor=white&style=for-the-badge" alt="Swift"/>
  <img src="https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white&style=for-the-badge" alt="TypeScript"/>
  </div>

</section>

---

<div class="home-section reveal">
  <div class="card">
    <h2>🧭 About Me</h2>
    <ul class="list-check">
      <li>Large-scale ingestion, background jobs, and domain-heavy systems.</li>
      <li>Currently building a flexible Alerts/Notification subsystem (polymorphic, fingerprinting/stacking, email jobs).</li>
      <li>Turn ambiguous requirements into production-ready features with tests & docs.</li>
      <li>Exploring Ruby gems, VS Code extensions, iOS prototypes, and Sanskrit NLP side projects.</li>
    </ul>
    <p class="muted">Current interests: performance tuning for CSV/S3 pipelines, Elasticsearch batching, Sidekiq cron/topology, and developer ergonomics.</p>
  </div>
</div>

<div class="home-section reveal">
  <div class="grid">
    <div class="card">
      <h3>Data Axle (2021–Present)</h3>
      <p>Boosted product revenue by 20%; streamlined validation to handle 1B+ records in two quarters; reduced deployment costs by 5%.</p>
    </div>
    <div class="card">
      <h3>Performance & Scale</h3>
      <p>Memory-safe ingestion pipelines; +10% data throughput per quarter with Rails, Sidekiq Pro, AWS, and Elasticsearch.</p>
    </div>
    <div class="card">
      <h3>Engineering Practices</h3>
      <p>TDD focus (RSpec/Minitest/Capybara), clean architectures, RESTful APIs, and scalable backend design.</p>
    </div>
  </div>
  <p class="center muted">Impact: measurable revenue growth, reduced costs, and successful high-traffic deliveries.</p>
</div>

<div class="home-section reveal">
  <div class="card">
    <h2>🧰 Toolbox</h2>
    <div class="chips">
      <span class="chip">Ruby</span>
      <span class="chip">Rails</span>
      <span class="chip">Java</span>
      <span class="chip">Spring</span>
      <span class="chip">TypeScript</span>
      <span class="chip">Node.js</span>
      <span class="chip">PostgreSQL</span>
      <span class="chip">Elasticsearch</span>
      <span class="chip">Redis</span>
      <span class="chip">AWS</span>
      <span class="chip">Docker</span>
      <span class="chip">TDD</span>
      <span class="chip">Observability</span>
      <span class="chip">Sidekiq</span>
    </div>
  </div>
</div>

<div class="home-section reveal">
  <div class="card center">
    <h2>📫 Contact</h2>
    <p>
      <a class="btn btn-primary" href="https://github.com/MridulS-R">GitHub</a>
      <a class="btn btn-ghost" href="https://www.linkedin.com/in/mridul-shukla-1a335818a/">LinkedIn</a>
    </p>
  </div>
</div>

<p class="center muted">Profile views counter omitted for faster loads and privacy.</p>

---

## Latest Posts

{% assign latest = site.posts | slice: 0, 3 %}
{% if latest and latest.size > 0 %}
<div class="grid reveal">
  {% for post in latest %}
    <div class="card">
      <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
      <p class="muted">{{ post.date | date: "%b %d, %Y" }}</p>
      {% assign blurb = post.description | default: post.excerpt %}
      {% if blurb %}<p>{{ blurb | strip_html | truncate: 160 }}</p>{% endif %}
    </div>
  {% endfor %}
</div>
{% else %}
<p class="muted">No posts yet.</p>
{% endif %}

---

## Recent Repositories

{% assign repos = site.github.public_repositories | where_exp: 'r', 'r.fork == false' | where_exp: 'r', 'r.archived == false' | sort: 'pushed_at' | reverse %}
{% assign repos = repos | slice: 0, 6 %}
{% if repos and repos.size > 0 %}
<div class="grid reveal">
  {% for r in repos %}
    <div class="card">
      <h3><a href="{{ r.html_url }}">{{ r.name }}</a></h3>
      {% if r.description %}<p>{{ r.description }}</p>{% endif %}
      <p class="muted">⭐ {{ r.stargazers_count }} · {{ r.language }} · Updated {{ r.pushed_at | date: "%b %Y" }}</p>
      {% if r.homepage %}<p><a href="{{ r.homepage }}">Live</a></p>{% endif %}
    </div>
  {% endfor %}
</div>
{% else %}
<p class="muted">No public repositories found or metadata not available in local build.</p>
{% endif %}
