# CLAUDE.md

This file provides guidance to Claude Code when working with code in this repository.

## Project

**[PROJECT_NAME]** — [one-sentence description of what the app/service does and who it's for]. [Primary platform, e.g. Android-first / web / CLI / API service].

**Status ([YYYY-MM-DD]):** [Current phase and brief summary of what's shipped and what's in flight. Keep this updated — it's the first thing Claude reads to orient itself.]

See **[PLAN.md](./PLAN.md)** for current phase, build checklist, and next action. Update it at the end of every session.

See **[explanations/INDEX.md](./explanations/INDEX.md)** for the session changelog. At the end of every session, write a new entry in `explanations/` following the conventions below.

**Starting a new session:** When the user says "let's continue" or similar, immediately read PLAN.md and the most recent file in `explanations/` before responding or taking any action.

---

## Explanation Workflow

At the end of every session, create a new file in `explanations/` and add it to `explanations/INDEX.md`.

**File naming:** `NNN-YYYY-MM-DD-slug.md` (e.g. `002-2026-04-01-auth-flow.md`)

**Sections:** Overview → Why This Exists → Technical Decisions → Dependencies → How It Fits Together → Gotchas → What's Next

**TTS writing rules — strictly follow these:**

- No code blocks, no inline backtick formatting
- No raw file paths — say "the auth configuration file in the library folder" not the path
- No raw URLs
- Spell out package names as spoken words
- Explain what packages do in plain English, not their package manager names
- Active voice, complete sentences, flowing paragraphs — write as if narrating
- Acronyms spelled out on first use

**Also at the end of every session:**

- Offer a one-line commit message summarizing the session's changes (don't run git commands — provide it for the user to use).
- If a release tag is being cut this session, offer a one-line annotated tag message too.
- If a [PLATFORM, e.g. mobile] version is being released, write/update the [STORE, e.g. Play Store] release notes as `[PATH_TO_CHANGELOGS, e.g. mobile/fastlane/metadata/android/en-US/changelogs/]<versionCode>.txt`.

---

## Working Style

- Be concise. Prefer concision to correct grammar.
- Make direct tech recommendations; don't present option lists.
- [USER_CONTEXT — e.g. "User is a DevOps engineer running a self-hosted home cloud — assume infrastructure competency."]
- Ask clarifying questions.
- Push back when necessary.

---

## Architecture

### Repository Structure

```
[PASTE YOUR MONOREPO STRUCTURE HERE]
```

### [Component 1, e.g. Mobile / Frontend]

- [Framework and key decision, e.g. "Expo (React Native) — offline-first, SQLite via expo-sqlite"]
- [Build notes — e.g. "Expo Go does NOT work (native modules); use npx expo run:android"]
- [Any gitignored / generated directories and how to regenerate them]

### [Component 2, e.g. Backend / API]

- [Framework and language]
- [Database]
- [Auth provider]
- [Storage / object store]

### [Component 3, e.g. Infrastructure]

- [Compose files and what each covers]
- [Services list]
- [How to run locally]

---

## Key Technical Decisions

- **[Decision name]:** [Why this was chosen and what it governs. Keep one bullet per major architectural decision so Claude doesn't re-litigate them.]
- **[Decision name]:** [...]
- **Full-stack changes:** any data model change (add/remove/rename a field) requires auditing both [COMPONENT_A] AND [COMPONENT_B] before writing — schema, types, API layer, sync layer, UI forms — then changing both together in one pass.

---

## Development Setup

### [Component 1]

```bash
[commands to build and run]
[commands to run tests]
```

### [Component 2]

```bash
[commands to install deps]
[commands to run locally]
[commands to run tests]
```

### [Component 3 / Infra]

```bash
[commands to spin up local stack]
```

[Access URLs for local services, e.g. API docs, admin panels, storage consoles]
