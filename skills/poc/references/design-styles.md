# Design styles + zero AI slop

Goal: the mock must look like **a real product designed by a human with taste**, matched to the specific app — not like a generic AI-spat template. Read this before you set colors/typography, and pick **one deliberate direction** from the library below.

## 1. What to NEVER do (AI-slop tells)

Each of these instantly reads as "made by AI". Banned by default:

| ❌ Slop | ✅ Instead |
|---|---|
| Gradient heroes / gradient buttons (purple→blue, coral→pink, rainbow) | **Flat, solid fills.** A gradient only if it's a deliberate brand element and subtle (duotone) — by default NO |
| Radial "glow"/blob/aurora/mesh gradient behind content | **Flat background**, one neutral color. No glowing patches |
| Decorative dots, ✨ sparkles, particles, floating shapes, background grids | **Nothing decorative.** Every element means something or it's gone |
| Everything centered (hero: big headline + subtitle + 2 buttons on the axis) | **Asymmetric hierarchy**, content left-aligned, one clear hero |
| XXL `border-radius`, identical on everything ("rounded everywhere") | Chosen, consistent radii. Sharper corners are fine too |
| Emoji as section headers and decorative bullets | Emoji only when it carries meaning (an action icon). The rest = typography / real icons |
| Glassmorphism / blur cards for no reason, a shadow under every element | **Flat surfaces + hairline borders.** Shadow only when functional (an element lifted above the rest) |
| Inter / Space Grotesk as the "safe" typeface for everything | A deliberate type pairing matched to the character (see the library) |
| Cream `#F4F1EA` + serif + terracotta | If editorial — **pick your own palette**, this is the most-copied AI look |
| Neon-green / acid on black as the only "pop" | An accent from the app's domain, not a "cyberpunk default" |
| Gradient text, glowing outlines, glow on buttons | Solid color. Contrast does the work, not effects |
| An accent bar/rail on the side of **every** card | Differentiate a card by background/border, not a rail on everything |

Positive core: **one chosen palette from the app's world, flat by default, one accent, boldness in one place, the rest quiet.**

## 2. How to choose a direction (don't randomize)

Ask yourself: *if this app were a real company — what would it look like?* Derive the direction from:
- **The industry** (medicine ≠ crypto ≠ wellness) — see the domain cheatsheet below,
- **The audience** (a senior ≠ a teenager ≠ a trader ≠ a factory operator),
- **The emotion** (trust / energy / calm / prestige / fun).

Then pick **one** direction from the library and stick to it consistently. Don't mix five.

## 3. Direction library

Each has ready tokens — plug them into the shell's variables (`--accent`, `--bg`, `--surface`, `--text`…).

### A. System / utility (clean, native — like iOS / Linear / Things)
- **When:** productivity, B2B tools, lists/tasks, "settings-heavy" apps.
- **Palette (light):** bg `#f6f7f9` · surface `#fff` · text `#16181d` · text-2 `#626875` · line `rgba(0,0,0,.08)` · one accent: `#2f6fed` or `#5b5bd6`. **Dark:** bg `#0f1115` · surface `#191c22`.
- **Type:** system (SF/Segoe/Roboto) — native, no webfonts.
- **Shape/depth:** radius 12–16, hairline borders, almost no shadows.
- **Motion:** minimal, 120–160ms.
- **Watch out:** this style lives on whitespace and precision — no gradients or glow.

### B. Premium dark (pro)
- **When:** fitness, analytics, media, premium fintech, sport, "power user".
- **Palette:** bg `#111318` (not pure black) · surface `#1a1d24` · text `#f4f5f7` · text-2 `#a7adba` · line `rgba(255,255,255,.08)` · one strong accent: coral `#ff5c39` / electric `#3d7bff` / lime only if it's the brand. High contrast.
- **Type:** strong grotesque / system, heavy weights on numbers, `tabular-nums`.
- **Shape:** radius 16–20, subtle light borders.
- **Watch out:** dark ≠ neon. One accent, not a rainbow. No glow blobs.

### C. Editorial / warm (your own palette, NOT the cliché)
- **When:** wellness, content, reading, food, a "human" brand.
- **Palette:** warm neutrals with character, but **NOT `#F4F1EA`**. E.g. sand `#efe9df` or cool paper `#f0f1ec`, ink `#23201b`, one muted accent: bottle green `#2f5d50` / plum `#6d3b5e` / ochre `#b5761f`.
- **Type:** a real serif for headings (Georgia/Charter — system-safe), sans for body. Generous margins, ~65 chars per line.
- **Shape:** small radii or sharp corners, thin lines, no shadows.
- **Watch out:** this is the most-copied AI look — if you go editorial, deliberately move the palette away from cream-and-terracotta.

### D. Bold / brutalist / high-contrast
- **When:** dev tools, crypto/web3, young brands, statements, events.
- **Palette:** clean blocks of color, strong contrast — black `#0a0a0a` / white `#fff` / one loud color: electric `#2b3aff` / red `#ff3b30` / yellow `#ffd400`.
- **Type:** heavy grotesque or mono, huge headings, mono for details.
- **Shape:** thick 2px borders, sharp corners (radius 0–6), a "hard offset" shadow instead of blur.
- **Watch out:** this is deliberate rawness, not lack of polish — keep the rhythm and consistency.

### E. Friendly consumer
- **When:** consumer apps, habits, fitness-lifestyle, education, kids.
- **Palette:** light warm background, one **friendly (not loud)** accent + 1–2 supporting, legible semantics.
- **Type:** a rounded/friendly sans (system rounded if available), legible weights.
- **Shape:** radius 16–22, soft but no neumorphism; light, functional shadow.
- **Watch out:** this is the EASIEST place to fall into slop — no gradient backgrounds, no sparkles, illustration only when purposeful.

### F. Data-dense / enterprise
- **When:** dashboards, admin, B2B SaaS, operational panels.
- **Palette:** neutral, calm; a sparing accent; semantics (ok/warn/crit) **separate** from the accent.
- **Type:** system, `tabular-nums` wherever there are numbers, dense but legible rows.
- **Shape:** small radii, hairline grids, minimal shadow.
- **Watch out:** information before decoration; encode state in form (pill/chip/bar), not color alone. Almost no motion.

### G. Minimal typographic / mono
- **When:** portfolio, high-end, tools for professionals, "less is more".
- **Palette:** black/graphite on off-white, color only functional.
- **Type:** one typeface, big type as the hero, a deliberate scale.
- **Shape:** sharp corners or minimal radii, lots of air.
- **Watch out:** spacing precision makes the whole thing — there's nowhere to hide.

## 4. Domain → palette (so the accent isn't random)

| Domain | Direction + accent |
|---|---|
| Health / medical | Calm blues `#2b7fff` / teal `#0e9e8e`, lots of white, no shouting → System or Friendly |
| Fintech / banking | Navy `#16233a` / money green `#12855a`, or premium black + 1 accent → Premium dark / System |
| Fitness / sport | Energetic: coral `#ff5c39`, electric blue, lime only as a brand; often dark → Premium dark |
| Productivity / B2B | Neutral + one confident accent (indigo/blue) → System |
| Education | Warm, friendly, legible, 1 accent + support → Friendly consumer |
| E-commerce / retail | Neutral background, the product is the hero, accent = brand/CTA color → System / Editorial |
| Social / community | Livelier accent, but a calm UI, content (people) up front → Friendly |
| Dev / tech / tooling | Mono accents, dark or high-contrast → Brutalist / System |

## 5. Common rules (so it isn't generic)
- **Neutrals with a slight bias** toward the accent — not pure gray `#808080`, add a touch of hue. A chosen neutral reads as "picked", not "inherited".
- **Flat by default.** Depth = a hairline border + maybe one functional shadow on the element that is genuinely "above" the rest.
- **Boldness in ONE place** (one hero per screen), the rest quiet. The accent doesn't fight the ground — if it does, drop saturation.
- **A deliberately paired typeface**, keep one type scale, headings `text-wrap: balance`.
- **Structure carries information, doesn't decorate.** 01/02/03 numbers only for a real sequence; dividers/labels only when they encode something.
- **Real data**, not placeholders — that's part of "not slop" too.
