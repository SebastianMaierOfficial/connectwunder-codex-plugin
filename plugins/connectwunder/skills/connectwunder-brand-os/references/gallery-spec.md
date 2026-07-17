# Brand OS Gallery specification

Build the Gallery as the visual companion to the ConnectWunder master document. It is a current-state reference and decision surface, not a second text-heavy brand guide.

## Purpose

Enable a human or AI collaborator to see:

- the current design DNA;
- how it changes across modes;
- confirmed colors, typography, rhythm, and components;
- real source evidence;
- genuinely open visual decisions;
- what should be produced next.

## Required sections

Adapt to scope, but normally include:

1. **Current direction:** concise positioning, current version, and status.
2. **Mode previews:** brand/content website, product marketing, landing page, software UI, designed document, and relevant media.
3. **Typography:** confirmed roles, real-language stress tests, long labels, responsive headlines, and special characters.
4. **Color and surfaces:** primitive values plus semantic use on dark and light backgrounds.
5. **Spacing and layout:** container, page insets, vertical rhythm, component gaps, and density examples.
6. **Logos and identifiers:** only approved or clearly open variants with usage context.
7. **Image and proof language:** photography, real product screens, diagrams, customer or partner evidence, and labelling rules.
8. **Motion and interaction:** durations, easing, state feedback, reduced-motion behavior, and haptics when relevant.
9. **Source inventory:** selected real references with status and learning.
10. **Open decision comparison:** only while a real decision remains unresolved.

## Visual rules

- Use actual or safely redacted assets instead of generic placeholders.
- Show the same content and dimensions when comparing candidates.
- Demonstrate desktop and relevant mobile widths.
- Show dense UI labels and form states for product typography.
- Show truthful proof near the claim it supports on landing-page examples.
- Demonstrate both dark premium surfaces and light reading or working surfaces when both are part of the system.
- Keep screenshots current and label legacy or concept screens clearly.
- Avoid decorative mockups that obscure the actual product.

## Language and typography tests

If the organization works in several languages, provide a language switch for representative copy.

Test:

- accented characters and locale-specific punctuation;
- long compound words and UI labels;
- uppercase labels and numerals;
- at least one real marketing headline;
- body copy;
- navigation, buttons, statuses, and form fields;
- responsive line breaks.

Do not approve a display font from an English-only specimen when the primary audience uses another language.

## Decision comparisons

When the user must choose:

- state the decision and recommendation;
- show no more than three viable candidates, preferably two;
- keep copy, width, size, spacing, and surrounding layout identical;
- explain the trade-off in one short note;
- include the actual target mode.

After confirmation, remove the comparison and all rejected candidate code. Replace it with one confirmed specimen.

## Sites workflow

Follow the Sites building and hosting skills.

1. Build in an isolated local project.
2. Read and reuse `.openai/hosting.json` when present.
3. Validate source, responsive behavior, accessibility, and production build.
4. Commit and push the exact validated source.
5. Package and save a Sites version.
6. Deploy privately by default.
7. Obtain explicit approval before a public or shared production deployment.
8. Poll deployment status until success or failure.
9. Add the deployed URL and Gallery version to the ConnectWunder master document.

Do not start another hosting stack when Sites meets the need.

## Privacy and access

Before sharing:

- remove personal data and private conversations from product screens;
- redact unreleased metrics, credentials, IDs, and customer information;
- verify rights for photos, logos, and external references;
- distinguish internal inspiration from assets licensed for production;
- label public, workspace-shared, or owner-only access.

If the Gallery cannot safely expose a source, show a redacted derivative or a written reference in the internal master only.

## Quality gate

Consider the Gallery ready when:

- it visibly matches the confirmed master document;
- every visual has a purpose and provenance;
- modes feel related but appropriately different;
- typography works in the real audience language;
- spacing and alignment appear intentional;
- mobile and dense UI cases remain usable;
- resolved alternatives are gone;
- the build succeeds;
- access matches the user's approval;
- the master document links to the current deployed version.
