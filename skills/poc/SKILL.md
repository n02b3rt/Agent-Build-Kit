---
name: poc
description: >-
  Build fast, clickable app mockups (mobile/web), prototypes and visualizations to validate
  an idea or demo a concept to a client — including live, during a conversation. Use THIS
  skill whenever the user wants to: build a clickable app mockup, show how something could
  look or work, visualize an idea for a client, or make a quick mockup. Trigger on phrases
  like "aplikacja mobilna do X", "apka do Y", "zbuduj mock", "pokaż jak to mogłoby wyglądać",
  "zwizualizuj pomysł", "szybki mockup dla klienta", "makieta aplikacji", "wireframe ekranu",
  "mobile app for X", "app for Y", "wireframe a screen", "build
  a mock", "show how this could look", "prototype for the client", "quick mockup", "zróbmy
  PoC", "proof of concept", "quick prototype" — even if the user never says the word "PoC".
  Especially: when the user describes an app and wants to see or click through it, this is the
  skill. It is for THROWAWAY / validation artifacts and concept demos, not for building the
  real production product (use the `kickstart` skill for that).
---

# PoC — fast clickable mockups for a PM

Turn an idea into something tangible, **live in a conversation**. A PoC is not a product — mock the data, cut corners, skip edge cases. One thing matters: does it show ONE thesis well enough to get a "wow". Working-and-now beats perfect-in-a-week.

(Technical feasibility or building it **for real** → not this skill, use `kickstart`.)

## Live fast path — SPEED FIRST (this is the default)

On `/poc live: <idea>` the client is often watching. **Get to a published EMPTY mock in seconds, then add features on request.** Do exactly this, nothing more:

1. **Pick the shell** from the idea: mobile app → `assets/mobile-shell.html`; website / web app / responsive → `assets/web-shell.html`.
2. **Copy** it to a working file. For the empty scaffold you only change `<title>`, the brand name, and one `--accent` (domain hints below) — nothing else.
3. **Publish** via `Artifact`. Reply with the link in **one line** + "what do we build first?". Keep the `file_path` + URL.

**At init, do NOT (this is what makes it slow):**
- **Do NOT read** `mock-canvas.md`, `design-styles.md`, `domains.md`, or load `artifact-design` / `dataviz`. Everything you need is inline in this file. Reading them first just makes the client wait.
- **Do NOT write an analysis** — no "Thesis / Surface / Direction / Assumptions" essay. Skip it entirely.
- **Do NOT deliberate** over the app name or ask about language. Default silently: name from the idea, content language = the language of the user's request (Polish for PL clients). At most one short line if you assumed something.
- **Do NOT invent features.** The first result is the empty, polished shell. Full stop.

The whole init = pick → copy → set title/accent → publish → one-line link + "what first?". Apply the anti-slop and golden rules below **silently** — don't narrate them.

**Phase 2 — features:** each user message = one change. Edit the same file, **republish to the same `file_path`** (same URL), no need to repeat `/poc`. The shell's header comment shows how to add screens/sections — glance at that if needed, not the reference files.

**Running on an existing app / repo?** Different job: read the app's current code and build an HTML replica of its key screens (so the client sees "what we have today"), then iterate. That's the one case where you read existing code before building.

## Always report state — one line, so the user knows what's happening
No walls of text. After every step, a single compact status line:
- **After init:** `🟢 Canvas live · <link> · empty — tell me what to add (e.g. "add the home screen").`
- **After each feature:** `✅ Added: <screen/section> · same link · now has: <comma-list of screens>.`
- **If you had to assume something** (name, language, accent): one short clause, e.g. `(assumed English + name "Ostrzyż" — say to change)`.
The user must always see three things: what's live, the link, and the next move. Nothing else.

## Anti-slop — inline, non-negotiable

The shell is already well-designed; keep it that way. **Flat by default, one accent from the domain, real data (never placeholders).** Banned: gradient heroes/buttons, glow/blobs behind content, decorative dots or ✨, everything-centered, emoji as section headers, glassmorphism, a shadow under everything, cream `#F4F1EA`+serif+terracotta.

Accent quick-pick: health → calm blue/teal · fintech → navy or money-green · fitness → coral (often dark) · productivity/B2B → indigo/blue · education → warm friendly · dev/tech → mono / high-contrast.

## Golden rules
- **Build only what was asked. Zero features ahead of time.**
- **"App" = show the product UI**, never a marketing hero/landing/pricing (unless explicitly asked).
- **Artifact = the app only** — no side panels or "assumptions" in the mock; assumptions go to the user in chat.
- **Real data** from the client's domain; **mock content in the client's/product's language** (Polish for PL clients).
- **Same link all session** — republish the same file.
- **Don't gold-plate** the shell — spend energy on features.
- **Web shell:** responsive CSS uses `@container`, not `@media`.

## Need more? (optional — read on demand, NOT before the first mock)
Reach for these only when a specific need comes up — never as a warm-up:
- `references/mock-canvas.md` — deep guide: incremental command vocabulary, building blocks, web `@container` details. Read when the shell's header comment isn't enough.
- `references/design-styles.md` — full direction library. Read only for an elaborate/branded look beyond the flat default.
- `references/domains.md` — per-domain "what to build / data / pitfalls".
- `artifact-design` skill — only for a bespoke visual beyond the shell. `dataviz` — only when adding a chart. `web-artifacts-builder` — complex multi-view React.
- `kickstart` — when the idea is validated and it's time to build for real.
