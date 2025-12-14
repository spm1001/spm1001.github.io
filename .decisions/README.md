# Architecture Decision Records

This directory contains ADRs documenting intentional design choices that might otherwise look like bugs, missing features, or code smell.

**Check these before "fixing" things that look wrong.**

## Index

| ADR | Summary | Key Files Protected |
|-----|---------|---------------------|
| [001-vibrant-js-removed](001-vibrant-js-removed.md) | Dynamic accent colors disabled for performance | `layouts/partials/footer/components/script.html` |
| [002-menu-animation-disabled](002-menu-animation-disabled.md) | Mobile menu has no slide animation (intentional) | `assets/scss/custom.scss`, `assets/ts/main.ts` |
| [003-reveal-layout-warning-ignored](003-reveal-layout-warning-ignored.md) | "No layout for reveal" warning is FALSE POSITIVE - do not fix | `hugo.toml`, `layouts/_default/single.reveal.html` |

## When to Add a New ADR

Create a new ADR when you:
- Remove a feature that upstream provides
- Disable functionality that users might expect
- Accept a warning/error as unfixable
- Make a non-obvious architectural choice

## ADR Format

```markdown
# ADR NNN: Title

## Status
Accepted/Superseded/Deprecated (date, commit)

## Context
Why this decision was needed

## Decision
What was decided

## Consequences
Trade-offs accepted

## DO NOT REVERT
Why future maintainers should not undo this
```
