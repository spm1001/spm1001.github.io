# ADR 001: Remove Vibrant.js

## Status
Accepted (2025-08-01, commit 59a1a73)

## Context
The hugo-theme-stack theme includes Vibrant.js to extract dominant colors from featured images and dynamically set accent colors per-page. This adds JavaScript weight (~16KB) and performs color extraction computation on every page load.

This site uses a consistent CRT green accent color (#00c000) as part of its visual identity. Dynamic per-image colors would undermine this consistency and add runtime cost for no benefit.

## Decision
Remove Vibrant.js by overriding `layouts/partials/footer/components/script.html` to exclude the Vibrant partial call present in the upstream theme.

## Consequences
- **Positive:** Reduced JavaScript payload, faster page loads, no runtime color extraction
- **Positive:** Consistent brand identity with CRT green accent across all pages
- **Negative:** Cannot use dynamic accent colors (not desired anyway)

## Files Changed
- `layouts/partials/footer/components/script.html` - overrides upstream, omits Vibrant
- `assets/ts/main.ts` - removed Vibrant-related imports (commit 59a1a73)

## DO NOT REVERT
This is an intentional performance optimization, not a missing feature. The upstream theme's script.html includes:
```html
{{- partial "helper/external" (dict "Context" . "Namespace" "Vibrant") -}}
```
Our override deliberately omits this line. Do not restore it.
