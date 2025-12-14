# Architecture

This document describes the technical architecture of spm1001.planetmodha.com, a Hugo-based static site.

## Dual-Theme Setup

This site uses two Hugo themes in overlay priority order:

1. **hugo-theme-stack** (primary) - Blog layout, styling, search, navigation
2. **reveal-hugo** (secondary) - Reveal.js presentation support

### How It Works

- Most pages use Stack theme layouts via `layouts/_default/baseof.html`
- Posts with `outputs: ["Reveal"]` in front matter use `layouts/_default/single.reveal.html`
- Stack provides: baseof.html, partials, SCSS foundation, search functionality
- Reveal provides: Reveal.js assets in `static/reveal-js/`

### Theme Configuration

```toml
# hugo.toml
theme = ["hugo-theme-stack", "reveal-hugo"]

[outputFormats.Reveal]
baseName = "index"
mediaType = "text/html"
isHTML = true
```

### Known Warning

Hugo emits a false positive warning about missing Reveal layout. See `.decisions/003-reveal-layout-warning-ignored.md`.

## Directory Structure

```
.
├── .decisions/          # Architecture Decision Records (ADRs)
├── archetypes/          # Templates for `hugo new` content
├── assets/
│   ├── icons/           # SVG icons for social links, navigation
│   ├── img/             # Site-wide images (avatar)
│   ├── scss/            # Custom SCSS (imports, variables, overrides)
│   └── ts/              # Custom TypeScript (menu, copy button)
├── content/
│   ├── page/            # Static pages (about, archives, search)
│   ├── post/            # Blog posts organized by year
│   └── tools/           # Interactive tools section
├── docs/                # Internal documentation
├── layouts/             # Hugo template overrides (see below)
├── static/              # Static files (favicon, manifest)
└── themes/              # Git submodules
    ├── hugo-theme-stack/
    └── reveal-hugo/
```

## Layout Overlays

Local layouts override theme defaults. Each overlay file has a header comment explaining its purpose.

| Local File | Purpose | Modification Level |
|------------|---------|-------------------|
| `layouts/partials/footer/components/script.html` | Remove Vibrant.js | Minimal |
| `layouts/partials/article/components/header.html` | LCP optimization + AVIF | Heavy |
| `layouts/partials/article-list/default.html` | Pass IsFirstArticle context | Minimal |
| `layouts/partials/footer/footer.html` | Formatting | Minimal |
| `layouts/partials/head/style.html` | CSS loading optimization | Moderate |
| `layouts/_default/single.reveal.html` | Reveal.js presentations | Custom (no upstream) |

### Overlay Sync Protocol

When updating the theme submodule:

1. Check `.decisions/` for intentional divergences that must be preserved
2. Compare each overlay file against new upstream version
3. Merge changes carefully, preserving custom functionality
4. Update `LAST SYNCED` comments in overlay headers
5. Update `$ThemeVersion` in `footer/footer.html`

## Intentional Divergences from Upstream

### Removed: Vibrant.js

The theme's dynamic color extraction (Vibrant.js) is disabled for performance.
See `.decisions/001-vibrant-js-removed.md`.

### Custom: Menu Animation

Theme's slide animation replaced with instant toggle for snappier feel.
See `.decisions/002-menu-animation-disabled.md`.

### Custom: Image Optimization

Custom AVIF/WebP pipeline with responsive images:

- `layouts/partials/helper/optimised_image_partial.html` - Core image processing
- `layouts/shortcodes/optimised_image.html` - Shortcode for content
- Generates 400px, 800px, 1200px variants in AVIF/WebP/fallback

### Custom: LCP Optimization

First article image loads eagerly with high fetch priority:

- `layouts/partials/article-list/default.html` tracks `isFirstArticle`
- `layouts/partials/article/components/header.html` sets `loading="eager"` and `fetchpriority="high"`

## Build Pipeline

### Local Development

```bash
hugo server -D --disableFastRender --logLevel error
```

- `-D` includes draft content
- `--disableFastRender` ensures clean rebuilds
- `--logLevel error` suppresses false positive warnings

### Production Build

GitHub Actions workflow (`.github/workflows/hugo.yml`):

1. Install Hugo extended (with AVIF support)
2. Checkout with submodules
3. Cache `resources/` directory (processed images)
4. Build with `--minify --gc`
5. Deploy to GitHub Pages

### Image Processing Cache

Hugo caches processed images in `resources/_gen/`. Configuration in `hugo.toml`:

```toml
[caches.images]
maxAge = "1h"              # Production
dir = ":resourceDir/_gen"

[development.caches.images]
maxAge = "24h"             # Development (less churn)
```

## Content Patterns

### Standard Blog Post

```markdown
---
title: "Post Title"
date: 2025-01-15
description: "Card/social media preview text"
summary: "RSS/LinkedIn lead-in text"
image: "cover.jpg"
categories: [Category]
---
```

### Reveal.js Presentation

```markdown
---
title: "Presentation Title"
date: 2025-01-15
outputs: ["Reveal"]
---

# Slide 1
Content

---

# Slide 2
More content
```

## RSS and Cross-posting

- RSS feed at `/index.xml` includes article summaries
- Zapier watches RSS and cross-posts to LinkedIn
- `summary` field appears as LinkedIn post text
- `description` field appears in URL preview card

See `README.md` for detailed RSS/LinkedIn integration notes.

## Performance Targets

- Google PageSpeed Insights: 95+/100
- Largest Contentful Paint (LCP): < 2.5s
- First Contentful Paint (FCP): < 1.8s

Key optimizations:
- Critical CSS inlining
- Eager loading for first article image
- AVIF/WebP with responsive srcset
- Deferred non-critical JavaScript
