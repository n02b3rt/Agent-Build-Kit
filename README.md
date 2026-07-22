# Agent Build Kit

A pair of agent skills that take you from idea to clickable prototype to a well-structured project — without the mess in between. Ships in [Claude Code](https://claude.com/claude-code) format today; works with any coding agent that supports skill-style instructions.

Built for product managers and anyone who needs to **validate a concept fast** (including live, during a client conversation) and then **turn it into a project that doesn't collapse as it grows**.

## Skills

| Skill | What it does |
|-------|--------------|
| **`poc`** | Builds fast, clickable app mockups (mobile / web) to validate an idea or demo a concept to a client. Works incrementally on a polished device shell, matches the design direction to the product's domain, and consistently avoids generic, "AI-looking" aesthetics. |
| **`kickstart`** | Sets up a new project on solid foundations — version control from the first minute, a consistent commit convention, a `CLAUDE.md` that acts as a living architecture map, and a `docs/` directory. Keeps the codebase navigable as it scales. |

## Requirements

- Claude Code (CLI, desktop app, web, or IDE extension)
- Git

## Installation

The skills install as user skills — copy them into `~/.claude/skills/` and Claude Code discovers them automatically.

**macOS / Linux**

```bash
git clone https://github.com/<your-user>/agent-build-kit.git
mkdir -p ~/.claude/skills
cp -r agent-build-kit/skills/poc       ~/.claude/skills/poc
cp -r agent-build-kit/skills/kickstart ~/.claude/skills/kickstart
```

**Windows (PowerShell)**

```powershell
git clone https://github.com/<your-user>/agent-build-kit.git
New-Item -ItemType Directory -Force "$env:USERPROFILE\.claude\skills" | Out-Null
Copy-Item -Recurse -Force agent-build-kit\skills\poc       "$env:USERPROFILE\.claude\skills\poc"
Copy-Item -Recurse -Force agent-build-kit\skills\kickstart "$env:USERPROFILE\.claude\skills\kickstart"
```

Restart Claude Code afterwards. Type `/` to confirm that the `poc` and `kickstart` commands are available.

## Usage

### `poc` — prototype / mockup

Start by describing the app:

```
/poc live: mobile app for tracking workouts
```

You get an empty device shell and a stable link. Add features one at a time, in plain language — the URL stays the same while the prototype grows in real time:

```
add a workout list screen
add a set counter to the workout screen
swap the data for a women's gym profile
```

### `kickstart` — new project

```
/kickstart new project: <name> — <one-line description>, stack: <technologies>
```

The skill initializes the repository, establishes the commit convention, and creates a `CLAUDE.md` with an architecture map plus a `docs/` directory. From that point on, every session and every new feature follows the same rules — including a fixed **repository language**, so the codebase never turns into a Polish/English mix regardless of the language you chat in.

## Design principles

- **Prototypes that look designed, not generated.** `poc` ships with a library of design directions and a hard set of rules that eliminate the usual "AI" tells (gratuitous gradients, decorative backgrounds, emoji as section headers). The style is chosen to fit the product's domain.
- **A foundation that survives growth.** `kickstart` captures project knowledge in files loaded at the start of every session (`CLAUDE.md` and `docs/`), so the project keeps a clear structure as it expands.
- **A clean history.** Concise, to-the-point commit messages; project configuration disables automatic tool-authorship trailers (`includeCoAuthoredBy: false`).

## Repository structure

```
skills/
├── poc/         SKILL.md · assets/ (mobile shell) · references/ (mock-canvas, design-styles, domains)
└── kickstart/   SKILL.md · assets/ (CLAUDE.md, settings, and docs templates)
```

## Updating

```bash
cd agent-build-kit && git pull
```

Then copy the contents of `skills/` into `~/.claude/skills/` again (as in *Installation*) and restart Claude Code.

## License

MIT — free to use and modify.
