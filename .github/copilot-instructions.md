# Copilot Workspace Instructions

These instructions apply to every session in this workspace. Follow them strictly.

---

## Design System — Non-negotiable

Always use the following. Never invent, approximate, or substitute.

**Components:** `@ux-aspects-universal/angular`
- Before using any component, read its README at:
  `node_modules/@ux-aspects-universal/angular/[component-name]/README.md`
- Full documentation (VPN required):
  `https://cybersecurity-enterprise.glpages.otxlab.net/ux-aspects/core/ux-aspects-universal/#/`

**Tokens:** `@jato/design-tokens`
- Use CSS variables for all colors, spacing, and sizing
- Never hardcode hex values, pixel values, or font sizes

**Typography:** `@jato/typography`
- Use JATO typography mixins and styles for all text
- Never define custom font sizes or weights

**Icons:** `@jato/icon-font` or `@jato/svgs`
- Never use external icon libraries

---

## Context Files

Before starting any design task, always read both files for the relevant product:

1. `_context/[product-name]/product-profile.md` — stable product knowledge
2. `_context/[product-name]/session-context.md` — current sprint focus

If either file is missing or has unfilled required fields, stop and ask the designer to fill them before proceeding.

---

## Skills Pipeline

Skills live in `.github/skills/design-pipeline/`. Always follow them in order:

1. `design-discover` — research, competitor scan, design directions
2. `design-conceptualize` — lo-fi wireframe concepts
3. `design-prototype` — hi-fi using design system components
4. `design-handoff` — annotated specs for engineering

Never skip a stage. Never proceed to the next skill if the current one has unresolved gaps.

---

## General Rules

- Always prefer existing patterns over inventing new ones
- Always flag assumptions explicitly — never silently assume
- Always use `unknown` in context fields rather than leaving them blank
- When sources conflict, follow the source of truth hierarchy in `product-profile.md`
- Accessibility standard: WCAG 2.1 AA minimum on all output
