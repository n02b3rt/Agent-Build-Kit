# Design fundamentals — proportions that make mocks look pro

Research-backed defaults (Apple HIG, Material Design, the 8pt grid, WCAG). **The shells bake these into CSS tokens — use the tokens, don't eyeball spacing.** Inconsistent spacing is the #1 thing that reads as "amateur".

## Spacing — the 8pt grid (non-negotiable)
Every padding / margin / gap is a step on the scale. Tokens in both shells:
`--s1 4 · --s2 8 · --s3 12 · --s4 16 · --s5 24 · --s6 32 · --s7 48 · --s8 64`
- Card padding: **16** (`--s4`). Gap between cards: **12–16**. Gap between sections: **24–32**.
- **Inner padding ≤ outer padding** — content sits comfortably inside its container.
- **≥ 8px between tappable elements** so taps don't collide.
- Whitespace is a feature. When unsure, add one more step — don't cram.

## Touch targets (mobile)
- Minimum tappable size **44×44** (iOS) / **48×48** (Android) — buttons, list rows, icon-buttons.
- Input / button height **44–48**. List row min height **44** with **16** padding.

## Type scale
- **Body ≥ 16px** for reading text (UI labels may go to 13–15, never smaller for content). **Line-height 1.4–1.5.**
- Scale by a ratio (**1.2 minor third** or **1.25**). Mobile tokens: `--t-cap 12 · --t-sm 13 · --t-body 16 · --t-lg 18 · --t-h3 20 · --t-h2 24 · --t-h1 30`. Web goes bigger: `--t-h1 40`.
- Headings **1.5–2× body**, heavier weight, `letter-spacing:-.02em` on large sizes, `text-wrap:balance`.
- Numbers that line up in columns: `font-variant-numeric: tabular-nums`.

## Web / responsive
- **Line length 50–75 chars, hard cap 80.** Body text container: `max-width: var(--measure)` (66ch). Never full-width paragraphs.
- Content container max-width **~1120–1200px**, generous side gutters (`--s5`/`--s6`).
- Fluid headings with `clamp(min, vw, max)` when you want them to scale.
- Web breakpoints in the web-shell use **`@container`** (not `@media`); common breakpoint ~**820px**.

## Layout hygiene
- One accent, **flat** surfaces, **hairline** borders (subtle `--line`, not heavy).
- Align everything to the one scale — consistency reads as "designed".
- Semantic color (ok/warn/danger) is separate from the accent.

Sources: [Apple HIG](https://developer.apple.com/design/human-interface-guidelines/layout) · [Material Design](https://m3.material.io/foundations/layout/understanding-layout) · [8pt grid — Cieden](https://cieden.com/book/sub-atomic/spacing/spacing-best-practices) · [Line length — UXPin](https://www.uxpin.com/studio/blog/optimal-line-length-for-readability/)
