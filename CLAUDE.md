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

## Site Overview

This is a Hugo-based static website for a personal blog/portfolio that generates content at https://spm1001.planetmodha.com. The site uses two themes: `hugo-theme-stack` (primary) and `reveal-hugo` (for presentations).

## Build and Development Commands

The site uses Hugo's built-in commands (no package.json present):

- **Build the site**: `hugo` (outputs to `public/` directory)
- **Development server**: `hugo server` (starts local development server)
- **Draft content**: `hugo server -D` (includes draft posts)
- **Force rebuild**: `hugo --cleanDestinationDir` (cleans output before building)

### Testing and Development Workflow
- **Always test changes locally** before pushing to production
- Use `hugo server -D --disableFastRender` for clean testing after code changes
- Claude Code can manage starting/stopping the hugo server process
- Test site at http://localhost:1313/ after any modifications
- Verify both visual appearance and generated HTML/CSS for performance impact

### Recent Session Progress (August 2025)
**Completed Code Quality Improvements:**
- ✅ Removed dead TypeScript intersection observer code (vibrant.js cleanup)
- ✅ Formatted compressed Hugo templates (index.html, archives.html) with proper indentation and comments
- ✅ Added explanatory comments for complex CSS edge-to-edge image techniques and CRT green color scheme
- ✅ Reduced unnecessary !important usage where possible
- ✅ All changes tested locally - site builds clean, no errors, performance maintained

**MCP Server Status:**
- browsermcp MCP server configured in .claude.json for visual site inspection
- Requires Claude Code restart to activate browser capabilities
- Will enable localhost visual testing and comprehensive site review

**Next Steps After Restart:**
- Test browsermcp MCP integration for visual site inspection
- Verify code improvements don't impact 95/100 PageSpeed score
- Continue any remaining code quality tasks if identified

## Architecture

### Directory Structure
- `/content/` - Markdown content files organized by type
  - `/post/` - Blog posts organized by year
  - `/page/` - Static pages (about, archives, search)
- `/layouts/` - Custom Hugo templates and partials
- `/assets/` - Source assets (SCSS, TypeScript, icons, images)
- `/static/` - Static files copied directly to output
- `/themes/` - Git submodules for Hugo themes
- `/public/` - Generated site output (not in git)

### Content Management
- Posts use front matter with `description` and `summary` fields
- `summary` appears in RSS feeds and LinkedIn cross-posts via Zapier
- `description` appears in site cards and social media previews
- Images are automatically processed to AVIF/WebP formats with fallbacks

### Themes and Layouts
- Primary theme: `hugo-theme-stack` for blog layout
- Secondary theme: `reveal-hugo` for presentation slides
- Custom layouts in `/layouts/` override theme defaults
- Dual output formats: regular HTML + Reveal.js presentations
- **IMPORTANT**: Never modify files in `/themes/` directory - use Hugo's overlay system instead
- Prefer minimal overlays to maintain theme compatibility during updates

### Git Submodules
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

### RSS and Cross-posting
- RSS feed generated at `/index.xml`  
- Zapier integration watches RSS and cross-posts to LinkedIn
- Uses `summary` field from front matter for social media text

### Image Optimization and Performance
- **Performance is critical** - Site maintains 95/100 Google PageSpeed Insights score
- Any performance regressions are unacceptable
- Automatic conversion to modern formats (AVIF priority, WebP fallback)
- Smart cropping and resizing via Hugo's image processing
- Complex image rendering code exists specifically for performance optimization
- Caching enabled for faster rebuilds (1h production, 24h development)
- Custom image partials handle responsive images with multiple format fallbacks