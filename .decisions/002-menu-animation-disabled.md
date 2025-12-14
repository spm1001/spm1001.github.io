# ADR 002: Disable Mobile Menu Animation

## Status
Accepted (2024, commit 74bbdcb)

## Context
The hugo-theme-stack theme includes `ts/menu.ts` which provides a slide animation for the mobile hamburger menu. The animation adds visual complexity and a brief delay when opening/closing the menu.

## Decision
Replace the theme's animated menu toggle with a custom implementation that shows/hides instantly. This is implemented in `assets/ts/main.ts` with corresponding CSS in `assets/scss/custom.scss`.

The custom implementation:
- Toggles `.show` class on `#main-menu`
- Toggles `.is-active` class on `#toggle-menu` (hamburger)
- Sets `aria-expanded` for accessibility
- Uses `transition: none !important` in CSS to ensure instant display

## Consequences
- **Positive:** Menu feels snappier and more responsive
- **Positive:** Simpler code path, no animation timing edge cases
- **Negative:** Loses the slide animation aesthetic (acceptable trade-off)

## Files Changed
- `assets/ts/main.ts` lines 17-33 - custom menu toggle implementation
- `assets/scss/custom.scss` lines 193-223 - mobile menu styling with `transition: none`

## DO NOT RESTORE ANIMATION
This is a deliberate UX choice. Do not import or re-enable the theme's `ts/menu.ts` animation behavior.
