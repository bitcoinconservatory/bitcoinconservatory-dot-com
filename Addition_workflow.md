# Content Addition Workflow

## Adding a New Lesson

1. Create a Markdown file in `docs/_lessons/`
2. Name it with the **blockheight** as the article ID prefix, e.g. `900000-my-article.md`
   - The blockheight is the Bitcoin block number at the time the article was created
   - This gives a natural chronological ordering
3. Add front matter at the top:

```md
---
title: "Your Article Title"
collection: lessons
categories:
  - basics
tags:
  - some-tag
---
```

4. Write your Markdown content below the front matter

## Assets (Images, Video, etc.)

- Place assets in `docs/assets/` using a matching directory or flat structure
- Every asset file name **must begin with the article ID (blockheight)** followed by a description
- Example for article `900000-my-article.md`:
  - `900000-diagram.png`
  - `900000-intro-video.mp4`
  - `900000-illustration-a.jpg`
- Reference assets in your Markdown using relative paths:

```md
![Description](../../assets/900000-diagram.png)
```

## What Happens Automatically on Build

- The new lesson becomes a page at `/learn/<slug>/`
- It appears on the **Learn** page (`/learn/`) as a listing
- It appears under its category on `/categories/#category-name`
- It appears under its tags on `/tags/#tag-name`
- No other file needs editing — just commit and push

## Page Roles

| Page | Purpose |
|------|---------|
| `/learn/` | Lists all lessons from `_lessons/` |
| `/categories/` | Groups lessons by category |
| `/tags/` | Groups lessons by tag |
| `/learn/<slug>/` | Individual lesson page |

## Naming Convention Summary

| Item | Pattern | Example |
|------|---------|---------|
| Lesson file | `blockheight-slug.md` | `900000-intro-to-arbitrary-data.md` |
| Image asset | `blockheight-description.ext` | `900000-diagram.png` |
| Video asset | `blockheight-description.ext` | `900000-intro-video.mp4` |

## Front Matter Fields

| Field | Purpose | Example |
|-------|---------|---------|
| `title` | Display title | `"Intro to Arbitrary Data"` |
| `collection` | Must be `lessons` | `lessons` |
| `categories` | Broad groupings | `[basics]` |
| `tags` | Specific topics | `[bitcoin, timechain]` |

## Filtering (Future)

- Filter by category or tag on the Learn page
- Sidebar navigation within the Learn section
- Explicit lesson ordering within a category via front matter `order` field
