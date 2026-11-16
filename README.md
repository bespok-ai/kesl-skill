# Kesl skill

Turns a task into a **Kesl runbook**: a short plan that [Kesl](https://kesl.ai), a web browser
with a built-in agent on your iPhone, carries out for you, with an **Open in Kesl** link that
hands it over. Booking, ordering, filling in a form, checking in: your AI writes the plan,
Kesl does the clicking.

It follows the open [Agent Skills](https://agentskills.io) format, so it works in Claude,
ChatGPT and any agent that reads skills. Install page: [kesl.ai/skill](https://kesl.ai/skill).

## Install

**Claude:** download `kesl.zip` from the [latest release](https://github.com/bcoughlin/kesl-skill/releases/latest),
then in claude.ai open **Customize › Skills** and upload it. Type `/kesl` to use it.

**ChatGPT (Work, web or desktop):** start a new session and send:

```
Help me install the following skill into my personal ChatGPT skill directory:
https://github.com/bcoughlin/kesl-skill/tree/main/skills/kesl
```

Or upload `kesl.zip` under **Settings › Plugins › Skills**. Type `@kesl` to use it. The web
and desktop apps keep separate skill lists.

**Coding agents** (Claude Code, Codex, Cursor and others):

```
npx skills add bcoughlin/kesl-skill
```

## Then

Ask for a Kesl runbook, for example: *"Make me a Kesl runbook to check in for my Delta
flight."* You get the runbook and an Open in Kesl link; tap it on your iPhone.

## Versions

Each release is tagged `vX.Y.Z`, and the version is in `SKILL.md` (`metadata.version`). What
changed in each one: [CHANGELOG.md](CHANGELOG.md).
