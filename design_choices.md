# Design Choices

## Principles

- **Minimal but expressive** — clean reading experience, no clutter, visual depth from SVG and curves not images
- **Organic and flowing** — soft bezier curves throughout, no hard geometric borders where curves serve
- **Static first** — no animations, no movement. Visual richness from composition alone
- **Responsive** — readable on mobile, expands gracefully on large screens without stretching body text

## Color Palette

| Token | Value | Purpose |
|-------|-------|---------|
| `--bg` | `#14161a` | Page background, near-black charcoal |
| `--bg-alt` | `#1a1d22` | Header, footer, alt surfaces |
| `--bg-surface` | `#1e2a36` | Cards, code blocks, elevated surfaces |
| `--fg` | `#e8e8e8` | Primary text |
| `--fg-muted` | `#8a96a0` | Secondary text, descriptions |
| `--slate` | `#153560` | Dark blue for glows and depth |
| `--slate-mid` | `#38547a` | Mid-tone blue for gradients |
| `--accent` | `#8ab4cc` | Links, highlights, curve strokes |
| `--accent-soft` | `rgba(138,180,204,0.12)` | Subtle tag backgrounds |
| `--border` | `#2a3440` | Card and section borders |

## SVG Curves

### Background layer
- Inline SVG via data URI on `body::before`
- Fixed position, full viewport, low opacity
- Multiple bezier paths with gradient strokes in slate tones
- Non-blocking to content, purely decorative

### Landing page
- Three-layer inline SVG curve between hero image and title
- Gradient fades from transparent → accent → transparent
- Radial glow behind hero image using `--slate`

### Article pages (`single.html`)
- Full-width flow divider between header and content area
- Subtle curve under article title with gradient stroke
- Both inline, zero external requests

## Typography

System fonts only for now. One or two web fonts planned for later addition.

## Layout

- **Reading width** capped at `44em` for body text
- **Max page width** expands to `64em` / `68em` on large screens for decorative space
- **Mobile** tightens padding, scales titles down, hides side nav
- **Glassmorphism** on header, footer, and cards (`backdrop-filter: blur`)

## Cards & Tags

- Lesson cards: rounded (`12px`), semi-transparent background, subtle hover lift
- Tags: pill shape (`999px` radius), soft accent background, hover fills solid
- All transitions are color-only, no movement animations

## What Was Avoided

- No external web fonts (yet)
- No raster background images for decoration
- No JavaScript for visual effects
- No breaking changes to the file-based article workflow
- No changes to `_config.yml`, `_includes/`, or markdown files

## Future Considerations

- Web font integration
- SVG filter or clip-path effects
- Subtle scroll-triggered reveals
- Tag/category filtering UI on the Learn page
