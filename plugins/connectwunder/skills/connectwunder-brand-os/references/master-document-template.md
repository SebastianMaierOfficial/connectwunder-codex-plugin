# Brand OS master document

Create one large, navigable Markdown document. Adapt the structure to the organization's actual scope; omit irrelevant sections rather than filling them with boilerplate.

## Recommended structure

```md
# Brand OS — Master

Stand: [date]
Status: [inventory / candidate / production]
Gallery: [URL and access level]

## Purpose
[What this system enables and which brands or channels it covers]

## How to use this document
[One source of truth, humans + AI, update and export rules]

## Current design DNA
[Short confirmed summary; clearly label hypotheses]

## Brand architecture
[Company, personal brands, products, offers, campaigns, endorsement rules]

## Visual inventory
[Entries with native images and evaluation]

## Confirmed foundation
### Color
### Typography
### Spacing and layout
### Surfaces, borders, radii, and shadows
### Logos and identifiers
### Photography and graphics
### Motion, interaction, and haptics

## Mode rules
### Brand and content websites
### Product marketing
### Landing pages
### Software products and backends
### Designed documents and marketing material
### Video and motion assets

## Patterns
[Hero, proof, CTA, article, navigation, sidebar, forms, tables, empty states, cover, timeline, etc.]

## AI production context
### Short context
### Production instructions by mode
### Negative rules

## Open decisions
[Only decisions that are genuinely unresolved]

## Migration rules
[What changes now, what changes on the next substantial update]

## Decision log
| ID | Decision | Reason | Scope | Status |

## Change log
[Version, date, change, reason]
```

## Inventory entry

Use this pattern for every meaningful source:

```md
### [Name]

![Descriptive visual](cw-asset://[asset-id])

| Field | Value |
| --- | --- |
| Type | Website / landing page / product UI / logo / document / media |
| Brand | [brand] |
| Status | Live / concept / legacy / inspiration |
| Source | [URL, file, design, or capture] |
| Captured | [date] |
| Evaluation | Keep / Improve / Phase out / Open |
| Next action | [bounded action] |

**What works:** [specific visual or functional strengths]

**What does not work / risk:** [specific weakness, inconsistency, or accessibility risk]

**Transferable learning:** [rule or hypothesis that can generalize]
```

Use descriptive alt text. Do not store a screenshot of an asset library when the actual relevant assets can be stored and evaluated individually.

## Confirmed token format

Prefer role-based tokens:

```txt
color.brand.navy.950
color.brand.gold.500
color.surface.page
color.surface.card
color.text.primary
color.text.on-dark
color.action.primary.background

font.family.display
font.family.sans
font.family.meta
font.size.display
font.size.body
font.line-height.display

space.1
space.2
space.3
layout.container.max
layout.page.inset
layout.section.gap

radius.control
radius.card
shadow.card
motion.interface.duration
motion.interface.easing
```

Document exact values only after confirmation. State the intended role and contrast requirements.

## Mode differentiation

Define shared DNA without cloning one layout everywhere:

- **Brand/content websites:** allow editorial typography, atmosphere, long-form reading, and personal authority.
- **Product marketing:** combine emotional positioning with real product proof and repeatable structure.
- **Landing pages:** prioritize conversion, objection handling, proof rhythm, and a clear action.
- **Software backends:** prioritize usability, hierarchy, density, accessibility, and state feedback; use brand expression selectively.
- **Designed documents:** translate the system into covers, timelines, frameworks, screens, decisions, and next steps rather than rigid slide templates.
- **Video/motion:** reuse typography, color, spacing, captions, lower thirds, transitions, and easing.

## AI production context

Write an operational context that another AI can apply without interpreting the inventory as permission.

Include:

- confirmed brand and mode;
- confirmed tokens and type roles;
- layout and spacing rules;
- permitted visual evidence;
- proof requirements;
- accessibility and localization;
- negative rules;
- migration or legacy warnings only when relevant.

Do not include rejected design candidates. Keep source observations in the inventory clearly separated from production instructions.

## Decision hygiene

While a decision is open, keep a clearly labelled temporary comparison in `Open decisions` and the Gallery.

After confirmation:

1. Replace the open comparison with the selected standard.
2. Remove rejected names and values from active guidance.
3. Remove unused font imports, components, tokens, and comparison code from the Gallery.
4. Add the selected decision, reason, scope, and migration rule to the log.
5. Rely on ConnectWunder version history for rejected candidates.

An existing project may retain a different value temporarily, but label it as a migration state rather than an option.

## Versioning

Create a new ConnectWunder document version for every meaningful change. In the edit summary state:

- what changed;
- why;
- affected modes or brands;
- whether migration is immediate or deferred;
- Gallery version when changed.

Use exact anchored patches for small edits. Use a full replacement only for intentional structural rewrites.
