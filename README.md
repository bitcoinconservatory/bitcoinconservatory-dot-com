# bitcoinconservatory-dot-com

Website for [bitcoinconservatory.com](https://bitcoinconservatory.com).

A simple Jekyll site served from `/docs/` on GitHub Pages. No external theme — just a few small layouts and one plain stylesheet.

## Add an article

Create a Markdown file in `docs/_lessons/`:

```md
---
title: "Your Article Title"
collection: lessons
categories:
  - basics
tags:
  - some-topic
---

Body text here, in Markdown.
```

- Each file becomes a page at `/learn/<slug>/`.
- `categories` and `tags` group articles on the Learn, Categories, and Tags pages.

## Files

- `_layouts/` — `default.html` (skeleton + nav + footer), `landing.html` (homepage), `single.html` (articles/pages)
- `_pages/` — Learn, Categories, Tags, Scholarship
- `_data/navigation.yml` — navigation
- `assets/css/main.css` — the single stylesheet
- `_config.yml` — site config and the `lessons` collection

## Build locally

```sh
cd docs
bundle install
bundle exec jekyll serve
```

(Site is served from the `docs/` folder, matching how GitHub Pages serves it.)
