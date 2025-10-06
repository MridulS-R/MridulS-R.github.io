---
layout: default
title: "Mridul Shukla — Senior Software Engineer"
image: "https://svg-banners.vercel.app/api?type=glitch&text1=Hello%20World!&text2=Senior%20Software%20Engineer&width=1600&height=350"
---

<section class="hero center">
  <h1 class="title">👋 Hi, I’m MRIDUL SHUKLA</h1>
  <p class="subtitle">Senior Software Engineer · Rails/Backend · Java/Backend · Python/Django</p>
  <p class="cta">
    <a class="btn btn-primary" href="{{ '/projects/' | relative_url }}">View Projects</a>
    <a class="btn btn-ghost" href="{{ '/blog/' | relative_url }}">Read Blog</a>
  </p>
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

## 🧭 About Me

- Worked on large-scale ingestion, background jobs, and domain-heavy systems.
- Recently building a flexible Alerts/Notification subsystem (polymorphic, fingerprinting/stacking, email jobs).
- Love turning ambiguous requirements into production-ready features with tests & docs.
- Exploring Ruby gems, VS Code extensions, iOS prototypes, and Sanskrit NLP side projects.

**Current interests:** performance tuning for CSV/S3 pipelines, Elasticsearch batching, Sidekiq cron/topology, and developer ergonomics.

---

## 🌟 Highlights

- Data Axle (2021–Present): Boosted product revenue by 20% in a few months by solving critical issues and aligning the product with customer needs. Streamlined validation processes to handle 1B+ data records in just two quarters, while reducing deployment costs by 5%.
- Performance & Scale: Built memory-safe ingestion pipelines that processed 10% more data per quarter, leveraging Rails, Sidekiq Pro, AWS, and Elasticsearch.
- Globant (2020–2021): Contributed to ESPN Golden Analyzers (Disney DTCI), delivering reusable Ruby gems that improved testing capacity and workflow usability for large-scale systems.
- MothersonSumi (2017–2019): Designed and deployed microservices (Kafka + Rails + Node.js) for RestaurantOS, and built a GST taxation module in Java/Postgres that scaled nationwide.
- Engineering Practices: Strong focus on TDD (RSpec/Minitest/Capybara), clean architectures, RESTful APIs, and scalable backend design.

> Impact: measurable revenue growth, reduced operational costs, large-scale data validation, reusable tooling for enterprise, and successful delivery of high-traffic platforms.

---

## 🧰 Toolbox

**Languages:** Ruby, Java, JavaScript/TypeScript, SQL, Swift (iOS), Bash  
**Frameworks / Runtimes:** Rails 6/7, Spring, Rack, RSpec & Minitest, Sidekiq, Redis, Node.js  
**Datastores:** PostgreSQL/MySQL, Elasticsearch, SQLite, S3 (data lake patterns)  
**Infra / DevOps:** AWS (S3, EC2, RDS, SQS, SES), Docker, GitHub Actions, Nginx  
**Practices:** TDD, Clean architecture, background job orchestration, observability (Honeybadger/Logs), performance profiling  

---

## 📫 Contact

- GitHub: [@mridul-shukla](https://github.com/MridulS-R)
- LinkedIn: [/in/mridul-shukla](https://www.linkedin.com/in/mridul-shukla-1a335818a/)


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
      {% if post.excerpt %}<p>{{ post.excerpt | strip_html | truncate: 140 }}</p>{% endif %}
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
