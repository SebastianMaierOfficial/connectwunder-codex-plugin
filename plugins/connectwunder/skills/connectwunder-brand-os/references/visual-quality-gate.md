# Visual quality gate

Run this gate on rendered output before a Brand OS design is confirmed or published. Review at the relevant desktop, tablet, and mobile widths after web fonts and images have loaded.

## Typography

- Judge optical distance between visible glyphs, not only CSS `line-height`. Inspect capitals, x-height, ascenders, descenders, umlauts, dots, punctuation, and the first and last glyph of every display line.
- Set high-impact display headlines as intentional line groups when automatic wrapping produces unstable rhythm. Apply small line-specific optical corrections when required; document them as composition adjustments rather than global spacing tokens.
- Test real audience language, long German compounds, umlauts, numerals, punctuation, buttons, and navigation labels.
- Verify that no line feels accidentally detached, crowded, clipped, or disproportionately wide. Reflow the copy before shrinking it beyond the intended hierarchy.

## Photography and crops

- Identify the primary subject and normalized focal point `(x, y)` for every image used with `object-fit: cover` or another crop.
- Record a short crop rule or safe area when a face, gesture, product, device, or proof detail must remain visible.
- Test the crop at every relevant aspect ratio. Use `object-position`, `<picture>`, or an art-directed derivative to keep the subject visible.
- If one crop cannot preserve both subject and composition, use a different image or separate derivatives. Never approve a layout that hides its main subject.

## Spacing and alignment

- Inspect visual groups in context: eyebrow to headline, headline to body, body to action, neighboring cards, image-to-copy transitions, and section boundaries.
- Check optical alignment in addition to box alignment. Icons, logos, rounded controls, and serif letterforms may need small corrections even when their bounding boxes match.
- Verify consistent page insets, intentional whitespace, and balanced density without forcing every section into an identical template.

## Approval record

Record the tested viewports, any deliberate optical or focal-point overrides, and remaining limitations in the Brand OS decision or change log. Treat failed checks as work to fix, not as optional polish.
