# {{PROJECT_NAME}}

{{ONE_LINER}}

**Stack:** {{STACK}}

> This file is the project's constitution. Read it **at the start of every session** — it defines how we work and where things live. Keep it short: it is an index; details go in `docs/`.

---

## Language convention (kills "Ponglish")

Three separate axes — do not mix them:

- **Repository language: {{REPO_LANG}}.** All code identifiers, comments, commit messages, documentation, and this file are written in **{{REPO_LANG}}** — **regardless of the language used in chat.** If someone chats in another language, the repository still stays in {{REPO_LANG}}. No mixing.
- **User-facing content: {{UI_LANG}}.** Text visible to end users (UI copy, labels, seed/demo data shown in the product) is written in **{{UI_LANG}}**.
- **Chat language:** whatever the person writes in. It has no effect on the two axes above.

When in doubt, the repository language wins for anything that lives in the repo.

---

## How we work (loop)

For every change:
1. **Understand** — check the "Project map" below and the relevant module / `docs/`. Read the code before you change it; don't guess.
2. **Plan a small step** — one logical change at a time.
3. **Build** — small files, single responsibility.
4. **Verify** — run / test that it works.
5. **Update the map/docs** — if a feature or module was added (see below).
6. **Commit** — short title, following the convention.

**Definition of done:** the code works **and** the map/docs are updated **and** it's committed. Without all three, the task isn't finished.

---

## Git — non-negotiable, from minute one

- **Repo from the start.** `main` is always in a working state.
- **Branches:** work on `feat/<short>`, `fix/<short>`, `refactor/<short>`, `chore/<short>`. Don't commit non-trivial changes straight to `main`.
- **Commit = one logical change.** Commit often, in small steps.
- **Commit title:** `type: short, on-point summary` (≤ ~60 chars), written in {{REPO_LANG}}. Types: `feat`, `fix`, `refactor`, `docs`, `style`, `test`, `chore`, `perf`.
  - `feat: email sign-in`
  - `fix: registration form validation`
  - `refactor: extract payment service`
- **No long body.** The title should be enough. Add a short body (2–4 bullets) **only** when the change is large / functionally important / non-obvious.
- **No AI/tool authorship, anywhere.** Never in commits, PRs, code, comments, or docs: no "Co-Authored-By", "Generated with", "AI", or tool names. This is also enforced by `.claude/settings.json` (`includeCoAuthoredBy: false`) — don't change it.

---

## Project map — WHERE THINGS LIVE  🔴 living index, update it with every feature

This is the antidote to the "colossus on clay feet". After adding **any** feature, add a row. Before building anything, check here whether it already exists.

| Feature / domain | Where (path) | Note |
|---|---|---|
| _(example)_ App configuration | `src/config/` | env vars, constants |
| _(example)_ Data layer / models | `src/…` | — |
| _(remove examples, add real rows)_ | | |

**Rule:** a new domain = a new module/folder + a row in this table. When a row gets too broad, split it.

---

## Architecture & documentation

Details live outside this file so it stays lightweight:

- **`docs/architecture.md`** — overview, main modules, data flow, key decisions. Read it before larger changes. Update it when the structure changes.
- **`docs/conventions.md`** — naming, folder structure, patterns, style, tests. Follow what's written there.
- Complex domain? Give it its own file in `docs/` (e.g. `docs/payments.md`) and link it from the map.

**Rule:** docs travel with the code. Change behavior → update the relevant `docs/`. Stale docs are worse than none.

---

## Healthy growth (so it doesn't become a colossus)

- **Small files, single responsibility.** A file that does two things or grows past ~300 lines → split it.
- **Module boundaries early.** One domain = one module. Don't mix layers (UI / logic / data) in one bag.
- **Don't duplicate** — check the map first to see whether the feature already exists.
- **Refactoring is normal work**, not "someday". Notice a mess in passing → clean it up and commit it separately.

---

## How to search the project (for the coding agent)

1. **Start with the map** — it tells you where things live. Faster than a blind grep.
2. Not in the map? → grep by domain/feature name, find it, **add it to the map**.
3. Read the module and its `docs/` before touching it.
4. Keep CLAUDE.md short — as it grows, move detail into `docs/` and leave only a pointer here.
