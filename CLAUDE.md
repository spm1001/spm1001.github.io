# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## General Working Preferences

### Communication Style
- Always explain what you're doing and why, so I can learn from the process
- **Do not apologize** - we're collaborating together, no need for excessive politeness
- Be direct and confident; walk through reasoning and decision-making
- **Avoid excessive enthusiasm** - don't gush about ideas, especially when you can't implement them
- Keep praise measured and realistic

### Development Workflow
- **Never commit or push changes** unless explicitly requested
- Make full use of available tools and automations rather than asking me to do things you can do
- When reverting changes, use `git` commands rather than manual file edits
- Be patient with multiple revision requests for visual/UX details

### Git Commit Messages
- Use neutral, descriptive language - avoid self-congratulatory terms like "clever", "brilliant", etc.
- Let the content speak for itself rather than editorializing about its quality
- Focus on what was done, not subjective assessments of how well it was done
- Example: "Antiques shop metaphor explaining header bidding" not "Clever antiques shop metaphor..."

### Platform Considerations (macOS)
- File paths often contain spaces - always use double quotes around paths in shell commands
- Example: `cd "/Users/modha/My Documents/project"` not `cd /Users/modha/My Documents/project`

### Code Quality
- Prioritize elegant, parsimonious solutions over quick fixes
- Use relative measurements rather than hardcoded dimensions
- Annotate changes with clear explanations of what was done and why
- When requesting manual file changes, provide complete file content

### Transparency
- Be explicit about limitations - if you cannot parse a screenshot, say so
- Pay close attention to artifacts like screenshots
- Don't pretend to have capabilities you don't possess

## Before Modifying: Check Decision Records

**IMPORTANT:** Before changing overlay files, SCSS, TypeScript, or build configuration, check `.decisions/` for Architecture Decision Records (ADRs) explaining intentional choices.

Things that look "broken" or "missing" may be intentional:
- Missing features may have been deliberately removed
- Warnings may be documented false positives
- "Suboptimal" code patterns may exist for good reasons

**Always check:** `.decisions/README.md` for an index of documented decisions.

Changes that "fix" documented decisions will break things.

## Site Overview

This is a Hugo-based static website for a personal blog/portfolio that generates content at https://spm1001.planetmodha.com. The site uses two themes: `hugo-theme-stack` (primary) and `reveal-hugo` (for presentations).

## Build and Development Commands

The site uses Hugo's built-in commands (no package.json present):

- **Build the site**: `hugo` (outputs to `public/` directory)
- **Development server**: `hugo server --logLevel error` (starts local development server, suppresses warnings)
- **Development server (full logging)**: `hugo server` (shows all warnings including the harmless Reveal.js warning)
- **Draft content**: `hugo server -D --logLevel error` (includes draft posts, minimal logging)
- **Force rebuild**: `hugo --cleanDestinationDir` (cleans output before building)
- **Clean testing**: `hugo server -D --disableFastRender --logLevel error` (recommended after code changes)
- **Quiet build**: `hugo --quiet` (completely silent build, errors only)

### Testing and Development Workflow
- **Always test changes locally** before pushing to production
- **Recommended development command**: `hugo server -D --disableFastRender --logLevel error` (clean rebuild, drafts, no false warnings)
- **For debugging**: Use `hugo server -D --disableFastRender` to see all warnings and logging details
- Claude Code can manage starting/stopping the hugo server process
- Test site at http://localhost:1313/ after any modifications
- Verify both visual appearance and generated HTML/CSS for performance impact

### Known Issues and Warnings

#### Reveal.js Layout Warning (False Positive)
**Warning:** `WARN found no layout file for "reveal" for kind "page"`

**Status:** **This is a known false positive - ignore this warning**

**Background:** 
- The functionality works correctly - Reveal.js presentations generate properly
- Hugo successfully finds and uses `layouts/_default/single.reveal.html`
- Only posts with `outputs: ["Reveal"]` in front matter use the presentation layout
- This warning appears to be a Hugo logging artifact from the dual-theme setup

**Historical Context:**
- Multiple fix attempts have broken search functionality, 404 pages, and template targeting
- Current configuration (commit b4bbb93) achieves the correct behavior:
  - `slides-you-get`: Renders as Reveal presentation ✓
  - `text-you-write`: Renders as Stack-themed blog post ✓
  - Search functionality works correctly ✓
  - 404 page uses Stack theme ✓

**Action:** Monitor but do not attempt to "fix" - functionality works perfectly despite the warning

## Architecture

### Directory Structure
- `/content/` - Markdown content files organized by type
  - `/post/` - Blog posts organized by year (2015-2025)
  - `/page/` - Static pages (about, archives, search)
- `/layouts/` - Custom Hugo templates and partials that override theme defaults
- `/assets/` - Source assets compiled by Hugo
  - `/scss/` - Custom SCSS (includes CRT green color scheme and responsive design)
  - `/ts/` - TypeScript (extends hugo-theme-stack with copy buttons, gallery, etc.)
  - `/icons/` - SVG icons for social media and UI elements
- `/static/` - Static files copied directly to output (favicons, manifests)
- `/themes/` - Git submodules for Hugo themes
- `/public/` - Generated site output (excluded from git)
- `/resources/` - Hugo's generated resources cache

### Content Management and Front Matter
- Posts require both `description` and `summary` fields in front matter
- `summary` appears in RSS feeds and LinkedIn cross-posts via Zapier
- `description` appears in site cards and social media previews
- Images are automatically processed to AVIF/WebP formats with responsive fallbacks
- All content is organized chronologically by year directories

### Themes and Layout System
- **Primary theme**: `hugo-theme-stack` for blog layout and styling
- **Secondary theme**: `reveal-hugo` for presentation slides
- **Dual output formats**: Regular HTML pages + Reveal.js presentations (see hugo.toml outputFormats)
- Custom layouts in `/layouts/` override theme defaults using Hugo's overlay system
- **CRITICAL**: Never modify files in `/themes/` directory - use Hugo's overlay system instead
- Prefer minimal overlays to maintain theme compatibility during updates

### Custom Styling and Components
- Custom SCSS implements CRT green accent color theme (`--accent-color: #00c000`)
- Dark sidebar with white article cards for optimal readability
- Responsive social icon styling with consistent sizing (24px)
- Mobile-optimized hamburger menu with green accent colors
- Custom avatar sizing and sidebar centering for visual balance

### Git Submodules Management
The themes are managed as git submodules:
```bash
# Initialize submodules after cloning
git submodule init
git submodule update

# Or clone with submodules
git clone --recurse-submodules [repo-url]

# Update submodules
git submodule update --remote
```

### RSS and Cross-posting Integration
- RSS feed generated at `/index.xml` with article summaries
- Zapier integration watches RSS and automatically cross-posts to LinkedIn
- Uses `summary` field from front matter for social media text
- LinkedIn integration requires careful front matter structure (see README.md)

### Image Optimization and Performance
- **Performance is critical** - Site maintains 95+/100 Google PageSpeed Insights score
- Any performance regressions are unacceptable and must be tested
- Automatic conversion to modern formats (AVIF priority, WebP fallback, JPEG/PNG fallback)
- Custom responsive image partial: `/layouts/partials/helper/optimised_image_partial.html`
- Three breakpoint sizes: 400px, 800px, 1200px for optimal loading
- Smart cropping and resizing via Hugo's built-in image processing
- Aggressive caching: 1h production, 24h development (see hugo.toml caches section)
- AVIF quality 60, WebP quality 60, JPEG/PNG quality 75 for size/quality balance

### TypeScript Architecture
- Main entry point: `/assets/ts/main.ts` (extends hugo-theme-stack functionality)
- Modular components: gallery, menu, color scheme, smooth anchors, scrollspy
- Copy-to-clipboard functionality for code blocks
- Global window objects exposed for theme compatibility
- No build process required - Hugo handles TypeScript compilation

### Hugo Configuration Highlights
- Dual theme setup with overlay priority
- Custom media types for Reveal.js presentations
- Image processing with AVIF/WebP support
- Google Analytics integration with privacy controls
- Related content configuration (threshold: 20, case-insensitive)
- Pagination set to 50 items per page