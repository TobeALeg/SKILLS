---
name: trekmind-ui-style
description: "Apply the TrekMind editorial UI design system to frontend work. Use when Codex needs to restyle an existing interface or build a new HTML, Vue 3, NextJS, or Tailwind frontend with TrekMind's paper-like editorial visual language: warm off-white backgrounds, ink typography, rust accents, serif-led hierarchy, tight component semantics, minimal radius, no shadows, generous whitespace, and divider-based layout."
---

# TrekMind UI Style

## Overview

Use this skill to build or refit frontends into the TrekMind visual language: editorial, restrained, warm, and text-led. Treat the bundled HTML as a visual reference, not as framework-specific source code to copy blindly.

## Workflow

1. Inspect the target project before editing: identify framework, styling entrypoints, existing design tokens, component conventions, and whether Tailwind is present.
2. Load `references/style-rules.md` for the non-negotiable visual rules.
3. Load `references/framework-adapters.md` for the target stack: HTML, Vue 3, NextJS, Tailwind, or an existing mixed setup.
4. If the user provided an existing UI, preserve its product flow and information architecture unless they asked for a redesign. Change visual language first.
5. If building from zero, create the usable product screen directly. Do not build a marketing landing page unless the user explicitly asks for one.
6. Before finalizing, check for drift from the TrekMind rules: no card-heavy SaaS look, no large rounded corners, no shadows, no unrelated accent colors, no cramped sections, and no copied one-off inline styles where a semantic class belongs.

## Required Style Moves

- Use the TrekMind tokens for paper, ink, and rust. Do not introduce extra brand colors unless the user's product domain truly requires status colors.
- Lead with serif typography for headings, body copy, insights, and narrative content. Use sans-serif for controls and system UI. Use mono for numbers, codes, and metadata.
- Create hierarchy with spacing, typography, dividers, and content width rather than shadows or decorative cards.
- Prefer semantic classes such as `.tm-eyebrow`, `.tm-rule`, `.tm-tag`, `.tm-btn-primary`, and `.tm-input` over repeating raw utility chains everywhere.
- Keep border radius at `2px` by default. Avoid pill buttons, soft SaaS cards, glow effects, gradient blobs, and purple/blue tech palettes.
- Make interfaces responsive, but keep the editorial rhythm: readable line lengths, generous section padding, and clear vertical sequencing.

## Resources

- `references/style-rules.md`: condensed TrekMind design rules, tokens, components, and visual prohibitions.
- `references/framework-adapters.md`: how to apply the same design system in HTML, Vue 3, NextJS, Tailwind, and existing projects.
- `assets/trekmind-base.css`: copyable CSS variables and base component classes.
- `assets/design-system-preview.html`: visual mother sample supplied by the user. Use it to understand rhythm and tone, not as a required page structure.
