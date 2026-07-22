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

## Live fast path — no extra reading needed

This is the default. Speed matters: get to a published mockup in one pass, **without reading the reference files or loading other skills first.** Everything you need for the first mock is here or in the shell's own header comment.

1. **Pick the shell.** Mobile app → `assets/mobile-shell.html` (iPhone). Website / web app / anything responsive → `assets/web-shell.html` (shows desktop + mobile at once — instant RWD).
2. **Scaffold (Phase 1).** Copy the shell to a working file; set `<title>` + the brand name + one `--accent` (domain hints below). Publish via `Artifact`; keep the `file_path` + URL. Give the link, ask "what do we start with?". **Don't invent features** — an empty shell is a valid first result.
3. **Grow (Phase 2).** Each user message = one change. Edit the same file, **republish to the same `file_path`** (same URL). No need to repeat `/poc`.

**The shell's header comment tells you how to add screens/sections and wire navigation — follow it.** Don't ask the user much; assume sensibly and say your assumption in chat so they can correct on the fly.

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
