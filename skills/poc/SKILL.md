---
name: poc
description: >-
  Build fast, clickable app mockups (mobile/web), prototypes and visualizations to validate
  an idea or demo a concept to a client — including live, during a conversation. Use THIS
  skill whenever the user wants to: build a clickable app mockup, show how something could
  look or work, visualize an idea for a client, or make a quick mockup. Trigger on phrases
  like "aplikacja mobilna do X", "apka do Y", "zbuduj mock", "pokaż jak to mogłoby wyglądać",
  "zwizualizuj pomysł", "szybki mockup dla klienta", "mobile app for X", "app for Y", "build
  a mock", "show how this could look", "prototype for the client", "quick mockup", "zróbmy
  PoC", "proof of concept", "quick prototype" — even if the user never says the word "PoC".
  Especially: when the user describes an app and wants to see or click through it, this is the
  skill. It is for THROWAWAY / validation artifacts and concept demos, not for building the
  real production product (use the `kickstart` skill for that).
---

# PoC — fast clickable mockups for a PM

This skill turns an idea into something tangible before anyone asks "so how would this look?". It's used by a PM whose most common task is to **show a client how something could look and work — often live, mid-conversation**.

Core principle: **a PoC is not a product.** You may mock data, cut corners, skip edge cases and the logic underneath. Only one thing matters: does this artifact **show a single thesis** well enough to get a "wow" and a reaction from the client. Working-and-now beats perfect-in-a-week.

(Want to check *technical feasibility* or build this **for real** as a project? That's not this skill — use `kickstart`.)

**Language of the mock's content:** default to the client's / product's language (Polish for PL clients) — ask if unclear. These skill instructions are in English, but the mock's visible text is written in the audience's language.

## How it works: a device shell, built incrementally

**You don't build the whole app at once.** You start from an empty, polished device shell and add features **one at a time, only when explicitly asked**. One tab = one stable link = an app that grows in front of the client.

**Before you start, read `references/mock-canvas.md`** — the full canvas guide (phases, how to add screens, building blocks, incremental commands, keeping the same URL). Read it once up front so you can then move fast.

### Shared start
1. **Capture ONE thesis.** State in one sentence: *what should this mock show?* That's the north star.
2. **Detect the surface.** Mobile app → copy `assets/mobile-shell.html` (iPhone shell). Website / web app / anything responsive → copy `assets/web-shell.html` — it shows the **same page on desktop and mobile at once**, so the client sees the RWD immediately. In the web shell write responsive CSS with `@container`, not `@media` (the shell provides the container; `@media` would look identical in both frames).
3. **Build** (see phases below).
4. **Deliver** — the link plus 2–3 sentences of "what this shows", a ready script to read to the client.

Ask about the idea **sparingly** — you're a PM, you have context. Instead of asking, make a reasonable assumption and **tell the user in chat** (not in the mock) so they can correct on the fly. Questions cost the most while a client is watching — there, assume and build.

### Flow (2 phases)
1. **Phase 1 — Canvas:** copy the shell to a working file, set the name + `<title>` + direction/accent (see `references/design-styles.md`), publish via `Artifact`, **remember the `file_path` and URL**. Give the link and ask "where do we start?". An empty shell is a valid Phase 1 result — **don't invent features.**
2. **Phase 2 — Features:** every following message from the user = one change. Edit the same file, **republish to the same `file_path`** (same URL). Within a session the user doesn't need to repeat `/poc`.

**Before you build anything visual, load the `artifact-design` skill.** For charts — `dataviz`.

### Golden rules (this is the core)
- **Build only what was asked. Zero features ahead of time.** Not asked → not in the mock.
- **App ≠ marketing page.** "App" = you show the product (the UI), never a hero/landing/pricing page, unless the user explicitly asks.
- **Artifact = the app only.** No side panels, notes, or "assumptions" in the mock — the client sees only the device. Assumptions and questions go to the user in chat.
- **Real data, not placeholders** — plausible names/amounts/dates from the client's domain.
- **Same link all session** — republish to the same `file_path`.
- **Don't gold-plate** — the shell is already pretty; spend energy on features, not on the frame's cosmetics.

## Quality bar
- **ZERO AI slop.** This is hard. Before setting colors/typography, read `references/design-styles.md` and pick **one deliberate direction** matched to the app. Banned by default: gradient heroes/buttons, radial "glow"/blobs behind content, decorative dots and ✨, everything-centered, emoji as section headers, glassmorphism for no reason, a shadow under everything, Inter/Space Grotesk for everything, cream `#F4F1EA`+serif+terracotta. Default: **flat fills, one accent from the domain, hierarchy, a chosen palette.** The mock must look like a real product designed by someone with taste.
- **Realistic data** instead of placeholders — the most important thing.
- **Polished enough, not pixel-perfect** — clean and bug-free on the happy path, but don't hunt pixels.
- **One thesis, one path** — resist scope creep.

## Skill files
- **`references/design-styles.md`** — a library of design directions + the AI-slop ban list (read before setting colors/typography).
- **`references/mock-canvas.md`** — the canvas guide (read at the start of a session).
- **`assets/mobile-shell.html`** — the iPhone shell (copy it, don't regenerate).
- **`assets/web-shell.html`** — the web shell: one responsive page mirrored to a desktop browser frame and a phone frame at once (RWD preview). Use `@container` for breakpoints.
- **`references/domains.md`** — "what to build / what data / pitfalls" recipes per domain.

## Use other skills
- `artifact-design` — always before building an Artifact.
- `dataviz` — before any chart/dashboard.
- `web-artifacts-builder` — complex React artifacts (state, routing).
- `product-management:*` — when the idea itself needs sharpening before the mock.
- `kickstart` — when the idea is validated and it's time to build the real project.
