# ADR 004: Dark Mode Toggle Disabled

## Status
Accepted (2024, configuration choice)

## Context
The hugo-theme-stack theme includes full dark/light mode toggle infrastructure:
- Toggle button in sidebar
- CSS variables for both schemes
- TypeScript class for state management
- localStorage persistence

The site uses a non-traditional color scheme:
- Dark sidebar (#222222) in both modes
- White article cards (#ffffff) in light mode
- The "light mode" already has a dark aesthetic

## Decision
Disable the dark mode toggle via `hugo.toml`:
```toml
[params.colorScheme]
toggle = false
default = "light"
```

## Rationale
1. **Visual identity:** The dark sidebar with white cards is the intended brand aesthetic
2. **Complexity vs value:** True dark mode would require careful retuning of the card colors, accent visibility, and image contrast
3. **Current scheme works:** The existing "light" mode already has dark elements, providing comfortable reading without a toggle

## Consequences
- **Positive:** Simpler UX, consistent brand appearance, no theme-switching edge cases
- **Negative:** Users who prefer dark mode don't get it (acceptable trade-off)

## To Re-enable
If you want to add dark mode later:
1. Set `toggle = true` in hugo.toml
2. Review `[data-scheme="dark"]` variables in custom.scss
3. Test card contrast (#282828 cards on #222222 background may be too subtle)
4. Verify accent color (#00c000) works on dark backgrounds

## Files Affected
- `hugo.toml` (lines 53-55) - toggle configuration
- `assets/scss/custom.scss` (lines 145-163) - dark mode variables exist but unused

## This Is Intentional
The infrastructure exists but is deliberately disabled. Do not "fix" by enabling the toggle without reviewing the color scheme implications.
