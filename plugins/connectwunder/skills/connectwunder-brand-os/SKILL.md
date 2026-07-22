---
name: connectwunder-brand-os
description: Build, audit, visualize, and maintain a living Brand OS in ConnectWunder. Use when a user wants to create or improve a brand guide, visual design system, brand inventory, AI-ready design context, or Brand OS Gallery from existing websites, product UIs, logos, documents, media, inspiration references, or a greenfield interview.
---

# ConnectWunder Brand OS

Create a living visual operating system rather than a static brand manual. Lead the user through an interview, collect evidence, build one ConnectWunder master document, create a visual Gallery with Sites, and maintain both as design decisions and production learnings evolve.

## Define the outcome

Build these artifacts:

1. **One ConnectWunder master document** as the current source of truth for humans and AI.
2. **One Brand OS Gallery** as the visual rendering of the current system.
3. **An optional ConnectWunder evolution board** only when the user wants a work queue or the number of open items warrants one.

Keep standards, inventory, visual references, decisions, migration rules, and AI production context in the master document. Do not split the active Brand OS across several documents merely for neatness.

Keep the board operational. Store tasks, evidence gaps, reviews, and migrations there; do not duplicate the guide.

## Enforce boundaries

- Perform every ConnectWunder workspace action through the ConnectWunder MCP tools. Never inspect or automate the ConnectWunder web app with a browser, except for a host-provided OAuth flow.
- Invoke the appropriate ConnectWunder read tool or `ping` on the first workspace action so the host can surface OAuth when needed.
- Use purpose-built connectors for external sources when available. Use browsing only for public website research or visual capture, never as a ConnectWunder fallback.
- Use the Sites building and hosting workflows for the Gallery. Reuse an existing `.openai/hosting.json` project when present.
- Publish the Gallery privately by default. Obtain explicit approval before public or otherwise open-world deployment.
- Never put confidential screens, personal data, unreleased product information, or unlicensed assets into a public Gallery.
- Do not invent brand decisions, asset provenance, logo permissions, customer relationships, or technical values.

## Explain the process

When the user asks what will happen, explain the loop in plain language:

> First we collect what exists or what inspires you. Then we evaluate it and extract recurring design DNA. The master document records the current rules and evidence; the Gallery makes them visible. We make unresolved decisions one at a time. Every new design is reviewed against the system, and useful learnings flow back into the next version.

Explain the benefit:

- Humans and AI start from the same current context.
- New websites, product UIs, documents, presentations, and media become faster and more consistent.
- Brands can retain distinct names and logos while sharing a recognizable design language.
- Decisions remain reversible and traceable without leaving rejected options in production context.
- The system improves through real projects instead of waiting for a perfect one-time rebrand.

## Run the workflow

### 1. Orient and interview

Read [references/interview.md](references/interview.md) before conducting the intake.

Ask progressively, in conversational batches of one to three questions. Reuse facts the user already supplied. Do not present a long questionnaire.

Support four valid starting paths:

- **Existing system:** websites, apps, logos, fonts, documents, videos, code, or design files already exist.
- **Inspiration-led:** the user supplies external examples and explains what they like or dislike.
- **Hybrid:** existing work and outside references both matter.
- **Greenfield:** little or nothing exists; derive an initial hypothesis from positioning, audience, preferences, constraints, and references.

Ask the user to provide any available URLs, ZIPs, screenshots, source files, logos, font files, Canva/Figma links, product screens, PDFs, presentations, social/video assets, and inspiration links. Accept partial input; do not block a useful first version on completeness.

### 2. Establish scope and coverage

Identify the brand architecture and relevant modes:

- company, personal brand, product brands, offers, campaigns, or endorsed sub-brands;
- classic brand or content websites;
- product-marketing websites;
- conversion landing pages;
- software backends and product UIs;
- designed documents and marketing materials;
- photography, graphics, motion, haptics, and video.

Distinguish shared design DNA from mode-specific behavior. A landing page may be bolder and proof-heavy; a software backend must prioritize usability, density, accessibility, and feedback. Do not force one identical surface across every mode.

Record coverage and missing evidence. Start decisions once the evidence is representative, not necessarily exhaustive.

### 3. Create the ConnectWunder master

Read [references/master-document-template.md](references/master-document-template.md).

Inspect existing documents, folders, and tags before creating anything. Reuse an existing Brand OS master when one exists. Otherwise:

1. Create one document named `Brand OS — Master`.
2. Place it in a clear Brand OS folder or tag when supported.
3. Create the initial full Markdown version.
4. Use exact anchored patches for later edits so unrelated wording stays stable.
5. Upload or register visual assets through supported ConnectWunder tools and embed the returned native references.

Treat native ConnectWunder assets as the canonical workspace copies. Preserve the original source link and provenance alongside each asset.

Do not assume a Markdown export makes `cw-asset://` media portable. When another AI or tool needs the Brand OS, provide either:

- the ConnectWunder document plus accessible Gallery URL; or
- an export bundle containing Markdown and the resolved image files.

### 4. Inventory before prescribing

For every meaningful source, record:

- name and type;
- brand and mode;
- current status;
- source and capture date;
- visual preview;
- what works;
- what does not work or creates risk;
- `Keep`, `Improve`, `Phase out`, or `Open`;
- transferable learning;
- next action.

Separate three layers:

1. **Observed fact:** what is visibly or technically present.
2. **User preference:** what the user likes, dislikes, or wants to protect.
3. **Confirmed standard:** what future production must use.

Inspect more than colors and fonts. Evaluate hierarchy, spacing rhythm, container width, edge insets, alignment, typography, imagery, proof, interaction states, responsive behavior, accessibility, localization, logo usage, and technical implementation.

### 5. Extract a design-DNA hypothesis

Summarize repeated strengths, tensions, and likely unifying principles. Treat this as a hypothesis until the user confirms it.

Define semantic tokens rather than isolated values:

- primitive and semantic colors;
- typography roles, weights, sizes, line height, and tracking;
- spacing and layout rhythm;
- radii, borders, shadows, and surfaces;
- motion durations and easing;
- product accents and status colors;
- logo roles and clear-space rules.

Document negative rules. State what the system must not produce, especially common generic-AI patterns, inconsistent spacing, decorative proof, weak contrast, random gradients, and new fonts or colors without a decision.

### 6. Build the visual Gallery

Read [references/gallery-spec.md](references/gallery-spec.md) before implementation.
Read [references/visual-quality-gate.md](references/visual-quality-gate.md) before approving or publishing any visual output.

Create the Gallery after the first useful inventory and design-DNA hypothesis exist. It must show the current system, not merely list rules.

Use real or safely redacted evidence where possible. Include a language switch and typographic stress tests when the brand serves more than one language or uses diacritics, long compound words, or non-Latin scripts.

Link the deployed Gallery from the master document. Record its current version and access level.

Do not confirm a layout from source code, tokens, or one static composition alone. Render the real content after fonts and images load, then run the visual quality gate at the relevant desktop, tablet, and mobile widths. A visibly uneven display headline or a crop that hides its primary subject blocks approval.

If Sites is unavailable, keep the visual inventory inside ConnectWunder and mark the Gallery as pending. Do not substitute an unapproved hosting provider.

### 7. Make decisions one at a time

For each meaningful open decision:

1. Explain why the decision matters.
2. Give one clear recommendation.
3. Show at most one or two genuinely viable alternatives when choice is necessary.
4. Compare candidates using identical content, dimensions, spacing, and context.
5. Test real language, responsive widths, product density, and relevant accessibility constraints.
6. Ask the user to choose only when judgment or brand preference is required.
7. Record the selected value, reason, scope, and migration rule.

Do not spend interview time on decisions that evidence already resolves safely.

### 8. Apply decision hygiene

Treat the active master document and Gallery as production context.

After a decision is confirmed:

- remove rejected alternatives from active rules, tokens, examples, comparison panels, prompts, source imports, and code;
- leave only the selected standard;
- preserve rejected candidates only in ConnectWunder version history or board activity;
- mark divergent existing work as a migration target, never as an optional standard;
- open a newly named decision round if the standard is reconsidered later.

Never leave a resolved comparison in material intended for another AI. A model may interpret any visible alternative as permission.

### 9. Maintain through production

When a new design project is created:

1. Supply the current master document and Gallery.
2. Review the output against confirmed rules and the relevant mode.
3. Add the output to the visual inventory.
4. Capture what worked, what failed, and what generalizes.
5. Update the standard only after a confirmed decision.
6. Add a migration rule for existing projects when needed.
7. Refresh and redeploy the Gallery when the visible standard changes.

Keep version summaries concise and outcome-focused. State what changed, why, where it applies, and when existing work should migrate.

## Use the optional evolution board

Create `Brand OS — Evolution` only with the user's approval or when requested. Recommended columns:

- Inbox / Evidence
- Needs review
- Decision ready
- Confirmed
- Migration
- Done

Each item should represent one bounded decision, evidence gap, or implementation. Link back to the relevant master-document section or Gallery view. Never make the board a second Brand OS.

## Complete a useful first version

Consider the initial Brand OS usable when:

- the relevant brand architecture and modes are mapped;
- representative source material is visually inventoried;
- preferences and confirmed standards are clearly separated;
- current tokens and rules are explicit enough for another AI to apply;
- the Gallery shows the current direction;
- unresolved items are named without masquerading as standards;
- the decision log and migration rules are present;
- the user knows how to use and evolve the system.

Report links to the ConnectWunder master document and Gallery, their access level, current coverage, and the next decision or evidence gap.
