# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## All commands run in Docker

Never run `bundle exec jekyll`, `gem install`, or any Ruby commands directly on the host. All tooling runs inside the container.

```powershell
# Start dev server (http://localhost:4000, LiveReload on 35729)
docker compose up -d

# Stop
docker compose down

# View logs / watch for build errors
docker compose logs -f jekyll

# Rebuild image after Gemfile changes
docker compose build && docker compose up -d

# One-off Jekyll command (e.g. build, doctor)
docker compose run --rm jekyll bundle exec jekyll build
```

## Architecture

This is a hand-built Jekyll 4.4 theme — no gem-based theme is used. Everything is defined locally.

### Sass compilation

Entry point: `assets/css/main.scss` (requires empty front matter `---` so Jekyll processes it).  
Partials live in `_sass/` and use **modern `@use`/`@forward` syntax** — never `@import`.  
Files that reference variables must include `@use 'variables' as *;` themselves; `main.scss` only pulls in `base` and `layout`.  
`_layout.scss` also imports `sass:color` for `color.adjust()` — use that instead of the deprecated `darken()`/`lighten()`.

### Category badges

Posts declare `category:` in front matter. `_layout.scss` generates badge colors via a Sass map (`$badges`) in `_variables.scss`:

```scss
$badges: (
  "announcement": #3b82f6,
  "news":         #10b981,
  "meeting":      #8b5cf6,
  "ctf":          #f59e0b,
);
```

To add a new category, add an entry to `$badges` — the `.category-badge--<slug>` class is generated automatically via `@each`.

### Adding content

New posts go in `_posts/YYYY-MM-DD-slug.md`. Front matter is intentionally minimal — only portable keys, no Jekyll-specific values:

```yaml
---
title: "Title"
date: YYYY-MM-DD
category: announcement  # announcement | news | meeting | ctf
---
```

`layout: post` is injected automatically via `defaults` in `_config.yml` and must not be added to individual post files. This keeps post files usable as-is if the site ever migrates to another SSG (Hugo, Eleventy, Astro, etc.).

Posts appear on the home page feed automatically, newest first.

### Layouts

- `default` — base HTML shell (head, header include, main, footer include)
- `home` — extends default; renders the post feed with category badges and excerpts
- `post` — extends default; renders a single post with badge + metadata header
- `page` — extends default; for static pages like About

### Key config

`_config.yml` sets `title`, `tagline`, `description`, and `permalink: /posts/:title/`. The `tagline` field is rendered in the header alongside the site title.

Once the GitHub Pages URL is known, set `url:` in `_config.yml` (e.g. `https://username.github.io`) so `jekyll-seo-tag` generates correct canonical URLs.

## Deployment

Pushing to `main` triggers `.github/workflows/deploy.yml` when any of these paths change: `_posts/**`, `_layouts/**`, `_includes/**`, `_sass/**`, `assets/**`, `_config.yml`, `Gemfile.lock`, or any `.md`/`.html` file. Adding a post file and merging to `main` is sufficient to trigger a deploy. `workflow_dispatch` is also available for manual runs.

The workflow:
1. Runs `actions/configure-pages` — automatically injects the correct `baseurl` for the Pages environment (handles both user pages and project pages)
2. Builds with `bundle exec jekyll build` using the locked Gemfile versions
3. Deploys via `actions/deploy-pages`

The Docker dev environment and the Actions build both use `Gemfile.lock` for identical gem versions. Do not delete `Gemfile.lock`.
