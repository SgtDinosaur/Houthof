# Copilot / AI agent instructions for Houthof 🔧

Purpose: Give immediate, actionable guidance for an AI coding agent to be productive in this small Jekyll site.

---

## Quick context (what this repo is)
- Static site built with **Jekyll** (theme: `minima`) and configured in `_config.yml`.
- Content is mostly Markdown pages (`index.md`, `about.markdown`) and posts in `_posts/`.
- Styles live in `assets/css/style.scss` (Sass processed by Jekyll). Images live in `assets/images/` and `images/`.
- Helpful dev artifact: `generate_images.html` (root and `assets/`) — a client-side script that creates downloadable sample images for the gallery.

---

## Quick start — commands you should use ✅
- Install Ruby gems (first time):
  - `bundle install`
- Run locally with auto-reload (recommended):
  - `bundle exec jekyll serve --livereload` (open http://localhost:4000)
- Build for production:
  - `JEKYLL_ENV=production bundle exec jekyll build`
- Notes:
  - Always use `bundle exec ...` to ensure the Gemfile-controlled versions are used.
  - If you change `_config.yml`, restart the server — Jekyll doesn't reload `_config.yml` automatically.

---

## Project structure & what to edit 🔍
- `_config.yml` — site settings (title, baseurl, plugins). Changing this requires restarting `jekyll serve`.
- `_layouts/default.html` — main HTML template that other pages use. Look here for shared header/footer HTML.
- `index.md` / other `.md` files at repo root — content pages using front matter (e.g., `layout: default`, `title:`).
- `_posts/` — dated blog posts (name format `YYYY-MM-DD-title.markdown`). Keep front matter consistent.
- `assets/css/style.scss` — global styles. Use the `.gallery` classes defined here when adding gallery items.
- `assets/images/` and `images/` — image assets referenced from templates and pages.
- `Gemfile` — controls Jekyll and plugin versions; changes here require `bundle install` / `bundle update`.

---

## Conventions & common patterns (use these, don't invent new ones) 📏
- Use Liquid's `relative_url` filter when emitting site URLs for portability, e.g.:
  - `{{ '/assets/images/wooden-building-1.jpg' | relative_url }}` (used in `index.md`).
- Markdown engine: `kramdown` (configured in `_config.yml`). Respect existing front matter patterns.
- Layout name usage:
  - Pages use `layout: default` (see `index.md`) — add or reuse the same layout unless a new layout is explicitly needed.
- Styling:
  - Keep styles in `assets/css/style.scss`. There are component classes already present (e.g., `.gallery`, `.gallery-item`, `.caption`). Reuse them for consistent look-and-feel.

---

## Integrations & external dependencies 🔗
- Plugins declared in `_config.yml` / `Gemfile`:
  - `jekyll-feed` and `jekyll-seo-tag` (installed through `github-pages` group in `Gemfile`).
- Deployment: intended for GitHub Pages (see `Gemfile` comment and `url` / `baseurl` in `_config.yml`). Pushing to `main` will publish the site if the repo is configured in GitHub Pages.

---

## Useful examples from this repo (copy/paste patterns) 🧾
- Image reference in templates/pages:
  - `<img src="{{ '/assets/images/wooden-building-1.jpg' | relative_url }}" alt="...">`
- New post format:
  - File: `_posts/2025-12-24-new-post.markdown`
  - Front matter:
    ```yaml
    ---
    layout: default
    title: "My Post Title"
    ---
    ```
- Run server with livereload:
  - `bundle exec jekyll serve --livereload` (useful for visual verification after edits)

---

## Debugging & PR checklist 🐞
- If pages are not picking up changes:
  - Restart `jekyll serve`, especially after modifying `_config.yml`.
- Asset not found or 404:
  - Check path (use `relative_url`) and ensure file is in `assets/` or `images/`.
- When changing dependencies or theme:
  - Update `Gemfile`, run `bundle install`, and verify local build with `bundle exec jekyll build`.
- PR checklist to include in PR description:
  - What changed (files & rationale)
  - Screenshot(s) or preview link of the affected pages
  - If dependencies changed, include `bundle update` output and any compatibility notes

---

## Notes and constraints ⚠️
- There are no automated tests or CI configuration in this repo — rely on manual visual checks and `bundle exec jekyll build` for validation.
- There are two copies of `generate_images.html` (root and `assets/`) — both are client-side helper pages; update both if you change the generator script.

---

If anything here is unclear or you want more/less detail (examples, commands, PR checklist items), tell me which sections to expand and I’ll iterate. ✅
