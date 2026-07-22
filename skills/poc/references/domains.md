# Domain recipes

Quick "what to build / what data / what pitfalls" for the product types you most often work on. Pick the section that fits the mock. Everything is built as a clickable Artifact (live mode).

> **Guard: app ≠ landing.** When the user is building an *app*, work from the "Web SaaS" or "Mobile" section and show the product (the UI). Take the "Landing / marketing" section **only** when the user explicitly asks for a page/landing/marketing site — never "along the way" while building an app.

---

## Web SaaS / dashboards

**What to show:** the thesis is usually "the right things are in the right place and you can act on them". Build one representative view: a header with key KPIs, a main table/list with real rows, one detail panel or action (filter, status change, drill-down).

**Data:** believable records from the client's domain — real company/person names, sensible amounts and dates, varied statuses (not all "OK"). 8–15 rows is enough to look real. Charts: **load `dataviz`**, use data with a real shape (a trend, not a flat line).

**How:** copy `assets/web-shell.html` — you'll see the dashboard on desktop and mobile at once. Use `@container` breakpoints so the layout reflows (sidebar collapses, wide table → stacked cards).

**Pitfalls:** empty/placeholder cells; every row identical; a chart with no axes/context; trying to build a whole CRUD instead of one convincing view.

---

## Mobile / apps

**What to show:** a flow across a few screens (e.g. onboarding, main action, confirmation). The thesis is usually "the path is simple / intuitive".

**How:** in live mode **copy `assets/mobile-shell.html`** (a ready iPhone shell with a screen router) and build incrementally per `references/mock-canvas.md` — add screens one request at a time, don't regenerate the frame. Large touch targets, real content, not a skeleton.

**Data:** content like a real app — notifications, names, avatars (initials/emoji instead of external images — the Artifact doesn't load external hosts).

**Pitfalls:** a "desktop" design squeezed into a phone; no transition state between screens (the client wants to see the *flow*, not a single screen); external images that won't load.

---

## Data / AI / automation

**What to show:** in the mock you show the *effect*, not a working engine — e.g. "an email comes in → the extracted invoice pops up", a pipeline as a diagram, a before/after view, a dashboard with the automation's result. The thesis: "this is how it would look and this is what it would give you".

**Data:** a realistic example of the result (extracted fields, classified records, a summary). You can hardcode the AI result — but **tell the user in chat that it's a fake**, so they don't promise the client a working engine.

**Pitfalls:** pretending the engine really works; showing only the ideal happy case with no room for an error/edge; overloading the screen with technicalities instead of a legible effect for the user.

---

## Landing / marketing / conversion flow

> Only when the user **explicitly** asks for a page/landing/marketing site. Building an app? → skip this section.

**What to show:** a complete, scrollable landing or funnel — a hero with a clear value proposition, benefit sections, a CTA, optionally a form (non-working, just the look) or a multi-step flow.

**Data:** believable copy from the client's domain (not "Your headline here"). Concrete benefits, plausible numbers/social proof. This sells the concept.

**How:** copy `assets/web-shell.html` so the client sees the landing on desktop and mobile at once. One nice scroll, `@container` breakpoints. Load `artifact-design`.

**Pitfalls:** filler text (lorem); vague CTAs ("Click here"); overload of sections — one strong narrative beats ten weak ones.
