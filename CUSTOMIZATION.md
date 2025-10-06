# Site Customization Guide

This guide lists practical steps to tailor your site (content, style, navigation, and automation) without digging through code.

## Content
- Edit homepage content in `index.md` (About, Highlights, Toolbox, Contact).
- Trim or reorder badge icons to your top skills for scannability.
- Update contact links and any headline copy you want emphasized.

## Projects
- Curate Featured first:
  - Edit `_data/featured.yml` and add items:
    - repo: owner/name
      title: Friendly Title
      blurb: One–two sentence description
      tags: [rails, sidekiq, redis]
      homepage: https://demo-or-site
      image: /assets/images/thumb.png (optional)
- Auto-listing uses `site.github.public_repositories` (forks/archived excluded) in `projects.md`.
- Optional (curation by topic): add the topic `portfolio` to repos you want to highlight, and filter to those only (ask to enable).

## Blog
- Create posts in `_posts/YYYY-MM-DD-title.md` with front matter:
  ---
  layout: post
  title: "Your Post Title"
  description: "One-sentence SEO blurb"
  tags: [rails, performance]
  ---
  Body text in Markdown. Place `<!--more-->` after the intro paragraph to control excerpts.
- Tags index: `/tags/`. Per-tag pages live in `tags/<tag>.md`:
  ---
  layout: tag
  title: "Tag: <tag>"
  tag: <tag>
  permalink: /tags/<tag>/
  ---

## Theme and Style
- Default: dark with a neutral grey background. Light mode via toggle or OS preference.
- Theme toggle persists in localStorage and updates browser UI color:
  - Logic in `_layouts/default.html` (header button and scripts).
  - CSS variables in `assets/css/style.css` use `html[data-theme="dark|light"]`.
- Tweak colors in `assets/css/style.css`:
  - Core: `--bg`, `--fg`, `--muted`, `--accent`, `--border`.
  - Hero gradient: `--g1`, `--g2`, `--g3` and the `.hero` block; animation speed via `@keyframes gradientShift`.
- Motion settings:
  - Reveal-on-scroll via an IntersectionObserver (layout script).
  - Respect reduced motion in CSS `@media (prefers-reduced-motion: reduce)`.

## Navigation
- Edit links in `_layouts/default.html` inside `<nav id="site-nav">`.
- Active states are automatic based on current page.
- We removed duplicate Projects/Blog CTAs from the hero; rely on navbar links.

## Homepage Modules
- Latest Posts block in `index.md`:
  - Change count via `{% assign latest = site.posts | slice: 0, N %}`.
  - Uses `description` or excerpt (after `<!--more-->`).
- Recent Repositories block in `index.md`:
  - Change count via `| slice: 0, N`.
  - Sorted by `pushed_at` and excludes forks/archived.
- Optional: add a Featured Projects strip on the homepage using `_data/featured.yml` (ask to wire in).

## SEO and Metadata
- Edit `_config.yml`:
  - `title`, `description`, `url` (e.g., https://username.github.io), `author` details.
  - `excerpt_separator: "<!--more-->"` is set for controlled summaries.
  - Plugins enabled: `jekyll-seo-tag`, `jekyll-sitemap`, `jekyll-feed`.
- For strong social previews:
  - Add an image (e.g., `assets/og-banner.png`) and set `image:` in page front matter.

## Automation (GitHub Actions)
- Repo cache (optional for richer project data): `.github/workflows/update-repos.yml`
  - Set repo secret `GH_TOKEN` (PAT with `public_repo`) to enable nightly fetch into `assets/data/repos.json`.
- Link checking: `.github/workflows/link-check.yml` runs weekly to find broken links.
- Issue → blog publishing: `.github/workflows/blog-from-issue.yml`
  - Use the issue template `.github/ISSUE_TEMPLATE/blog-post.yml` and label the issue `blog` to auto-create `_posts/YYYY-MM-DD-slug.md`.
- AI enrich (optional): `.github/workflows/ai-enrich-posts.yml`
  - Set repo secret `OPENAI_API_KEY` to get suggested description + tags on PRs that modify `_posts/**`.

## Local Preview
- Jekyll local build (optional):
  - Requires Ruby + Bundler and a `Gemfile` (ask to add if not present).
  - Serve locally: `bundle exec jekyll serve` then open `http://localhost:4000`.
  - For GitHub metadata locally: `export JEKYLL_GITHUB_TOKEN=<token>`.

## Deployment
- GitHub Pages should deploy from the default branch, folder `/ (root)`.
- After pushing changes, wait for the Pages build to finish; hard refresh the browser if styles look cached.

## Common Customizations (Checklist)
- [ ] Update site title and description in `_config.yml`.
- [ ] Add 3–6 Featured repos in `_data/featured.yml`.
- [ ] Write at least one blog post in `_posts/` with `description` and `tags`.
- [ ] Provide an OG image and set `image:` on important pages.
- [ ] Set `GH_TOKEN` (and optionally `OPENAI_API_KEY`) in repo secrets for automation.
- [ ] Adjust hero gradient and animation speed to taste.
- [ ] Review Projects auto-list and add a topic filter if desired.
- [ ] Verify tag pages exist for your common tags in `tags/`.

---

Need help applying any of the options above (e.g., topic filtering, thumbnails, resume page)? Ask and I’ll wire it in.
