---
title: "Accessibility for the Agent Era"
date: 2025-12-14
draft: true
categories: ["AI", "Design"]
tags: ["agents", "accessibility", "content-systems", "LLMs"]
---

Traditional accessibility asks: *Can people with different abilities access this content?*

This gave us screen readers, alt text, ARIA labels, keyboard navigation. The insight was that "the user" isn't monolithic - different people have different access needs, and good design serves them all without requiring separate versions.

## The New Dimension

We now have a second axis: *Can machines access this content?*

But "machines" isn't monolithic either. The machine might be:

- **My agent** (Claude on my desktop, with my credentials)
- **Someone else's agent** (Gemini in a colleague's browser, with their credentials)
- **A published artifact** (a Gem, a bot, a workflow - running in whose context?)

This creates a matrix:

|  | **Self** | **Other** |
|---|---|---|
| **Human** | Me reading/editing | Colleagues reading |
| **Machine** | My Claude, my scripts | Their Gemini, shared Gems |

Traditional web design optimised for one cell: other humans reading. Developer tools (APIs, CLI) optimised for another: self's machines. We rarely designed for all four simultaneously.

## The Insight

**Agents inherit identity context.**

When a sales person's Gemini queries for information, it runs as that person. It sees what they see. It can't see my private docs, or content behind auth it doesn't have.

This is different from a web crawler or a search index. Those are infrastructure - they see everything and serve results based on access control. An agent in someone's browser is a *principal* - it has an identity, permissions, and context.

The question shifts from "is this content machine-readable?" to "can this content be reached by agents operating in different identity contexts?"

## The Design Implications

### 1. Separate Store from View

Content should live in a canonical store that supports multiple views:

- A rendered website for human reading
- API access for technical users' agents
- Index/connector integration for non-technical users' agents

The store is the truth. Views are projections optimised for different principals.

### 2. Auth-Aware Content Placement

If you want someone's agent to see content, it must live somewhere that agent can reach with that person's identity.

- **Google Docs** → visible to Workspace Gemini (because Gemini inherits Drive access)
- **Internal wiki behind SSO** → invisible to Workspace Gemini (it can't authenticate)
- **Indexed into Discovery Engine** → visible to Gemini Enterprise (by design)

The content's location determines which agents can see it.

### 3. Don't Bifurcate, Multiply Views

The solution isn't "put everything in one place that works for everyone" - because no single interface works for everyone. The solution is: one source, multiple views, each optimised for its principal.

- MIT edits Markdown in Git (optimised for technical authors + their agents)
- Static site renders it beautifully (optimised for human readers)
- Custom connector indexes it (optimised for non-technical users' agents)

Same content. Three access patterns. No bifurcation because they're all views of one source.

### 4. Design for the Whole Matrix

When creating any content system, ask:

| Principal | How do they reach this? | Is that path good? |
|---|---|---|
| Me (human) | Direct access | ? |
| My agents | API, filesystem, MCP | ? |
| Others (human) | Shared link, published site | ? |
| Others' agents | Their identity context → ??? | ? |

The last cell is the one we forget. And it's increasingly important as agents become the default interface to information.

## The Philosophical Shift

Accessibility was about removing barriers for humans with different abilities.

Broadened accessibility is about removing barriers for principals with different contexts - where a principal might be a human, an agent acting on behalf of a human, or an artifact serving many humans.

The elegance criterion remains: solutions that serve multiple principals without separate paths are better than solutions requiring per-principal infrastructure.

When we build for the matrix, we build for a world where "who is accessing this?" has a richer answer than it used to.

---

*Distilled from a conversation about wiki architecture, December 2025*
