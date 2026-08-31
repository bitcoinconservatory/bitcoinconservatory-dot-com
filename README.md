# bitcoinconservatory-dot-com

Website for bitcoinconservatory.com

Served from `/docs/` and built with Jekyll on GitHub Pages using a small set of custom layouts and a plain-CSS dark, minimalist theme (no external theme dependency).

## Content

Articles and lessons live in `docs/_lessons/` as Markdown files with YAML front matter:

```yaml
---
title: "Lesson Title"
collection: lessons
categories:
  - basics
tags:
  - topic-a
  - topic-b
---
```

- Each file becomes a page at `/learn/<slug>/`.
- `categories` / `tags` drive the Learn, Categories, and Tags index pages.

## Layout

- `_layouts/default.html` — base skeleton (nav + footer)
- `_layouts/landing.html` — homepage
- `_layouts/single.html` — article/lesson and archive pages
- `assets/css/main.css` — single plain stylesheet
