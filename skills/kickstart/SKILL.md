---
name: kickstart
description: >-
  Set up a new software project on solid foundations and keep it clean as it grows: git from
  the first minute (repo, branches, commit convention), a CLAUDE.md project constitution, a
  living architecture map of "where things live", a docs/ structure, and healthy-growth rules
  — so the project doesn't turn into a colossus on clay feet. Use THIS skill when the user:
  starts a new project / repo, says "nowy projekt", "zacznijmy projekt", "init", "setup
  projektu", "kickstart", "new project", "set up a repo", "let's build this for real", "move
  from PoC to a real project", or starts coding something meant to live longer than one mock.
  It also configures a fixed repository language (kills "Ponglish") and removes any AI/tool
  authorship from commits and docs. This is NOT for one-off PoCs (use the `poc` skill) — it's
  for real, growing projects.
---

# kickstart — a solid project foundation

This skill exists so a project has, **from the start**, the hygiene that keeps it navigable after 3 months and 200 commits. You validated the idea with a mock (`poc`) — now you're building it for real, and you want to avoid the classic failure: it grows, loses structure, and every new feature becomes archaeology.

The solution in one sentence: **git from the first minute + a `CLAUDE.md` with a living project map + `docs/` that grow with the code + small-module discipline.**

## Phase 1 — Setup (done once, at the start)

Confirm with the user (if not given): project name, one-line description, stack, **and the languages** (step 1). Then:

1. **Set the languages first — this kills "Ponglish".** Two axes, independent of the chat language:
   - **Repository language `{{REPO_LANG}}`** — code, identifiers, comments, commits, `docs/`, README, `CLAUDE.md`. **Default English** (recommended: LLMs and developers work best in it, and the repo reads professionally). Propose English and confirm.
   - **User-facing content language `{{UI_LANG}}`** — text visible in the app, copy, seed data. Default: the product's/audience's language (e.g. Polish).
   - **The chat language stays as-is** — you don't set it; you still reply to the user in their language. Typical setup: they write in Polish, the repo is English, the UI is Polish. **The repo stays in `{{REPO_LANG}}` regardless of the chat language.**
2. **Git.** If there's no repo → `git init`. Create a `.gitignore` matched to the stack.
3. **Project settings.** Copy `assets/settings.template.json` → `.claude/settings.json` (disables "Co-Authored-By" → `includeCoAuthoredBy: false`).
4. **CLAUDE.md.** Copy `assets/CLAUDE.template.md` → `CLAUDE.md` and fill `{{PROJECT_NAME}}`, `{{ONE_LINER}}`, `{{STACK}}`, `{{REPO_LANG}}`, `{{UI_LANG}}`. The templates are canonical **in English**; if `{{REPO_LANG}}` ≠ English, translate the content on write. Leave the map with 1–2 real rows to grow.
5. **Docs & journal.** Copy `assets/architecture.template.md` → `docs/architecture.md`, `assets/conventions.template.md` → `docs/conventions.md`, and `assets/AI_NOTES.template.md` → `AI_NOTES.md` (repo root). Fill the placeholders (`{{DATE}}` = today, plus the languages). Same translation rule.
6. **Skeleton.** A minimal folder structure for the stack (e.g. `src/`), only as much as needed — don't build ahead.
7. **First commit** on `main`: `chore: project scaffold` (title in `{{REPO_LANG}}`). Short, no body, **no AI/tool mention**.
8. **Working branch** for the first feature: `git checkout -b feat/<short>`.
9. Tell the user: the foundation is ready, languages are set, from now on the rules in `CLAUDE.md` apply — and off you go with the features.

## Phase 2 — Development (applies in every later session)

The rules live in the project's `CLAUDE.md` (read it at the start of every session). Summary:

- **Languages:** repo in `{{REPO_LANG}}` (code, commits, docs), UI content in `{{UI_LANG}}` — stick to it **regardless of the chat language**. No Ponglish.
- **Git:** branches `feat/ fix/ refactor/ chore/`; commit = one logical change; title `type: short and on-point` (≤ ~60 chars), no long body except for large/important changes. **No AI/tool mention anywhere.**
- **Project map:** after adding each feature, add a "where it lives" row in `CLAUDE.md`. Before building, check whether the feature already exists.
- **Docs with the code:** you change structure/behavior → update `docs/`. A complex domain gets its own file in `docs/`.
- **Journal (`AI_NOTES.md`):** read it at the start of every session; at the end of every larger task add a dated entry (what was done, decisions, watch-outs). It's the memory that survives context resets.
- **Context handoff:** when a session gets long and the model starts looping or nears the token limit, don't push on — reset. Dump the state (the ready prompt is in `CLAUDE.md`), open a fresh chat, paste it, continue. Capture the same in `AI_NOTES.md`.
- **Plan before non-trivial work:** write reasoning in `<plan>…</plan>` (edge cases, bugs, alternatives) before the solution — it cuts hallucinations. Skip only for trivial one-liners.
- **Healthy growth:** small files (single responsibility, split when >~300 lines or doing 2 things), module boundaries, no duplication, refactor as you go.
- **Definition of done:** the code works **and** the map/docs are updated **and** it's committed.

## Why this works (so you don't do it blindly)

A "colossus on clay feet" happens because knowledge about the project lives only in someone's head (or in one session's context) and evaporates. This skill **materializes that knowledge in files that are always at hand**: `CLAUDE.md` (map + rules, loaded at the start of every session) and `docs/` (details). So every later session — yours or another developer's — starts with the full picture instead of reconstructing it each time. A map updated with every feature means "where do I add this / where do I find it" has an answer in 5 seconds, not after 20 minutes of grepping.

## Skill files
- `assets/CLAUDE.template.md` — the project constitution (map, git rules, growth).
- `assets/settings.template.json` — `.claude/settings.json` that blocks AI/tool authorship (`includeCoAuthoredBy: false`).
- `assets/architecture.template.md`, `assets/conventions.template.md` — `docs/` skeletons.
- `assets/AI_NOTES.template.md` — running project journal, read at session start and updated after larger tasks.

## A note on git
Keep commits clean and frequent. Don't add `--no-verify` or bypass hooks without an explicit request. Never put any AI/tool mention in commits, PRs, or docs — that's a hard rule of this skill.
