---
name: design-discover
description: >
  Runs the discovery stage of the design pipeline. Use this skill when a designer
  starts a new feature, problem, or sprint. Triggers on: "run design-discover",
  "start discovery", "I need to design [feature]", "I want to start working on [feature]",
  "help me design [feature]", or when a designer opens a session-context.md file.
  Always run this skill before design-conceptualize. Never skip discovery.
---

# Design Discover

Runs structured discovery on a design problem. Produces clearly defined design
directions the designer can carry into conceptualization.

---

## Before You Start

Check which mode to run based on feature scope:

**Lightweight mode** — for small features, minor improvements, or well-understood problems:
- Runs: `problem-framer` → `direction-synthesiser`
- Tell the designer: "Running in lightweight mode — problem framing and directions only.
  Use full mode for significant features or when user and constraint signals are unclear."

**Full mode** — for significant features, new flows, or complex problem spaces:
- Runs all five agents in sequence
- Tell the designer: "Running in full discovery mode — this covers problem framing,
  user signals, constraints, precedents, and directions."

**How to decide:**
Ask the designer: "Is this a small improvement or a significant feature?"
If unsure, default to full mode.

---

## Step 0 — Validate Context

Before running any agent, check both context files exist and are filled:

1. `_context/[product-name]/product-profile.md`
2. `_context/[product-name]/session-context.md`

Ask the designer: "Which product are you working on?"
Then check the corresponding `_context/[product-name]/` folder.

**If either file is missing:**
Stop. Tell the designer:
"I need your product context before starting discovery.
Copy the templates from `templates/` into `_context/[product-name]/`
and fill in both files. Start with `product-profile.md` if this
is a new product, or just `session-context.md` if the profile already exists."

**If required fields are blank:**
Stop. List exactly which fields are missing and ask the designer to fill them.
Do not proceed with incomplete context.

**Required fields — product-profile.md:**
- Public name
- What this product does
- Primary user roles
- Core jobs-to-be-done
- Source of truth hierarchy

**Required fields — session-context.md:**
- Problem statement
- Why now
- Success looks like
- What exists today

---

## Step 1 — Problem Framer

Read: `.github/skills/design-pipeline/design-discover/agents/problem-framer.md`

Run the agent against the validated context files.
Present output to designer before proceeding.

Tell the designer:
"Here's how I've reframed your problem. Review the assumptions —
if anything is wrong, correct it before I continue."

Wait for designer confirmation before moving to Step 2.

---

## Step 2 — User Signal Extractor
*(Full mode only)*

Read: `.github/skills/design-pipeline/design-discover/agents/user-signal-extractor.md`

Run the agent against context files and problem-framer output.
Present output to designer before proceeding.

Tell the designer:
"Here's what we actually know about your users versus what we're assuming.
Review the gaps — if you have additional signals I haven't seen, add them
to session-context.md and I'll re-run this step."

Wait for designer confirmation before moving to Step 3.

---

## Step 3 — Constraint Mapper
*(Full mode only)*

Read: `.github/skills/design-pipeline/design-discover/agents/constraint-mapper.md`

Run the agent against context files and all previous agent outputs.
Present output to designer before proceeding.

Tell the designer:
"Here are the constraints shaping your design space. Pay attention to
hard blockers — any direction that conflicts with these is not viable.
If any constraint is wrong or missing, update your context files now."

Wait for designer confirmation before moving to Step 4.

---

## Step 4 — Precedent Scanner
*(Full mode only)*

Read: `.github/skills/design-pipeline/design-discover/agents/precedent-scanner.md`

Run the agent against context files and all previous agent outputs.
Use web search for competitor research if available.
Present output to designer before proceeding.

Tell the designer:
"Here are relevant precedents from your product suite, competitors,
and adjacent industries. These will inform the directions — not dictate them."

Wait for designer confirmation before moving to Step 5.

---

## Step 5 — Direction Synthesiser

Read: `.github/skills/design-pipeline/design-discover/agents/direction-synthesiser.md`

Run the agent against all previous outputs.
Present all directions to the designer.

Tell the designer:
"Here are [N] fundamentally different directions for your problem.
These are not ranked — you decide which to take forward.
When you've chosen, say 'run design-conceptualize on direction [N]'
to move to the next stage."

---

## Handoff to Design Conceptualize

When the designer has chosen a direction, produce a handoff summary:
Save this as `_context/[product-name]/discovery-handoff.md`.
Tell the designer: "Discovery complete. Your handoff summary is saved.
Run design-conceptualize when ready."

---

## Rules

- Never skip Step 0 — incomplete context produces wrong directions
- Never proceed past any step without designer confirmation
- Never recommend a direction — designer decides
- Always declare the mode being run and why
- Always save the handoff summary before closing discovery
- If a designer tries to skip discovery and go straight to prototype, refuse politely:
  "Discovery ensures we're solving the right problem. Skipping it risks
  building the wrong thing well. It takes less time than a redesign."
