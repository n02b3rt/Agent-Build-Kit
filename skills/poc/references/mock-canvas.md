# Mock canvas — building incrementally on a device shell

This is the working method for `live` mode when mocking apps (mobile / web). Philosophy: **we don't build a full app in one shot.** We start from an empty, polished device shell and add features **one at a time, only on explicit request**, clickable, in front of the client. One browser tab = one stable link = an app that grows during the conversation.

## Two phases

**Phase 1 — Canvas.** The user says *what* they're building (e.g. "a mobile app for tracking workouts"). You:
1. Detect the surface: mobile → `assets/mobile-shell.html`. (Web app chrome — coming; until it lands, build web the classic way, but keep the same incremental discipline.)
2. Copy the shell to a working file (scratchpad), e.g. `poc-<name>.html`.
3. Set the identity: `<title>`, `.poc-appname`, the project accent (`--accent`).
4. Publish via `Artifact` → **remember the file path and the URL**. That's the stable link.
5. Give the user the link and ask: **"which screen/feature do we start with?"**. **Don't invent features.** An empty shell with a nice empty state is a valid Phase 1 result.

**Phase 2 — Features.** Every following message from the user = one change. Add/change **only that**, editing the same file, and **republish to the same `file_path`** (same URL). The client refreshes / watches the same tab.

Within one conversation the user does **not** need to repeat `/poc` — you're already on the canvas, so "add screen X", "swap the data for a clinic", "remove the streak" are enough.

## Golden rules (this is the core of this mode)

1. **Build only what was asked. Zero features ahead of time.** Don't add sign-in, settings, empty states, or "handy" screens. If the user didn't ask — it's not in the mock. Extra screens dilute the message and steal time.
2. **App ≠ marketing page.** When the user says "app / tool", you show **the product (the UI)**. Never a marketing hero, "about us", pricing, or landing page — unless they explicitly ask. Their goal is to show the app *working*, not to sell it.
3. **Real data, not placeholders.** Plausible names, amounts, dates, statuses from the client's domain. "Lorem ipsum" and "Item 1" kill a PoC.
4. **Same link the whole session.** Republish to the same `file_path`. A stable URL is the killer feature — the client keeps one tab open and watches it grow.
5. **Don't gold-plate.** The shell is already pretty. Don't fiddle with the frame/status-bar cosmetics — put your energy into the features the user wants.
6. **Clickable, not static.** Wire every new screen into navigation (`data-go`) so you can reach it and go back.

## How to add a screen (mobile-shell)

Insert screens between the `POC:SCREENS-START` / `POC:SCREENS-END` markers. When you add the **first real screen**, the router auto-hides the empty state and shows the tab bar.

```html
<section class="poc-view" data-screen="home" data-default>
  <div class="poc-appbar"><h1>Home</h1></div>
  <div class="poc-card"> ...content... </div>
</section>
```

- `data-screen="id"` — unique screen identifier.
- `data-default` — the starting screen (give it to one, usually the first/main one).
- **A primary screen (a tab-bar destination)** → also add a nav item between `POC:TABS`:
  ```html
  <button class="poc-tab" data-go="home"><span class="ic">🏠</span><span>Home</span></button>
  ```
- **A detail screen** (reached from a list, not the tab bar) → give it a `data-screen` but **don't** add it to the tab bar. Navigate with an element carrying `data-go="detailId"`, and a back button: `data-go="back"` (the router keeps history).

Navigation works on its own: **any** element with `data-go="id"` navigates to that screen. Don't write your own screen-switching JS — the shell's router handles it. You also have `window.POC.go(id)` / `window.POC.back()` if you need it from code.

## Building blocks (already in the shell — use them, don't reinvent)

| Class | Purpose |
|---|---|
| `.poc-appbar` (+`<h1>`, `.back`, `.sp`) | Screen top bar; `.back` = back button, `.sp` = spacer |
| `.poc-card` | Basic content container (white rounded surface) |
| `.poc-sec` | Section heading (small, uppercase) |
| `.poc-btn` / `.poc-btn.ghost` | Primary / secondary button (full width) |
| `.poc-row` (+`.ic`,`.tl`,`.st`,`.chev`) | List row: icon + title + subtitle + chevron. Great as a `data-go` into a detail |
| `.poc-pill` / `.ok` / `.warn` | Status markers |

Color tokens (use the variables, not hardcoded hex): `--accent`, `--bg`, `--surface`, `--surface-2`, `--line`, `--text`, `--text-2`, `--text-3`, `--ok`, `--warn`, `--danger`. Changing `--accent` recolors the whole thing and keeps the theme consistent.

**Charts / dashboards in a screen:** load the `dataviz` skill before drawing any chart. Use data with a real shape (a trend), not a flat line.

**Direction + accent per project:** in Phase 1, pick **one deliberate direction** from `references/design-styles.md` matched to the app and set the tokens with it (`--accent`, `--bg`, `--surface`, `--text`…). **Flat by default** — no gradient heroes, no glow blobs behind content, no decorative dots. One accent, the rest neutral. This is hard: the mock must not look AI-generated.

## Web shell (`web-shell.html`) — desktop + mobile at once

For websites / web apps, copy `assets/web-shell.html` instead of the mobile shell. It renders **one** responsive page in two frames side by side — a laptop browser and a phone — so the RWD is visible at a glance ("here's desktop, here's mobile").

- **Edit only inside `<template id="poc-app">`.** The shell mirrors that single page into both frames; you never touch the frames themselves.
- **Breakpoints use `@container`, NOT `@media`.** Both frames share the same viewport, so `@media` would look identical in both. The shell makes each frame a query container — write e.g. `@container (min-width: 820px){ …desktop… }`, with the mobile layout as the base rules.
- **Add sections** into `<main class="main">`; **nav** into `.side` (desktop sidebar) and `.topnav`. The default skeleton already reflows (sidebar → hidden, top nav → hamburger), so RWD shows the moment you open it.
- **CSS-first.** If a section needs JS, put it in the shell's bottom `<script>` and attach it to every `.poc-app-root` (there are two copies).
- Same golden rules as mobile: build only what's asked, real data, flat design, one stable URL all session.

## Incremental command vocabulary

Recognize these naturally and make the **minimal** change:

- **"add screen/feature X"** → one new section (+ a tab if it's a main destination).
- **"add X to screen Y"** → append an element to section Y only.
- **"change / fix X"** → edit the existing element, nothing else.
- **"remove X"** → delete the section/element and its nav entry.
- **"swap the data for domain/client X"** → replace content with that domain's reality, layout stays.
- **"show the empty / error / loading state of Y"** → a variant of an existing screen, if the user asks.
- **"change the accent to X" / "make it dark"** → tokens in `:root` (dark: see the "DARK APP" comment in the shell).

After each change: republish the same file and **briefly** say what was added (1 sentence) + that the link is unchanged. No long reports — conversation pace matters more.

## What NOT to do

- Don't regenerate the phone frame / status bar — copy the shell.
- **Don't add a side panel / notes / "assumptions" to the artifact** — you show the device only (the client is looking at it live). Assumptions and questions go to the user in chat.
- Don't add screens "because they fit". Wait for the request.
- Don't build a landing page when building an app.
- Don't change the `file_path` between iterations (it would change the URL).
- Don't clutter with placeholders.
