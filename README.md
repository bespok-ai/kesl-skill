# Kesl skill

Have [Kesl](https://kesl.ai), the web browser with a built-in agent on your iPhone, do
something for you: check a flight, look something up on a live site, fill in a form, book or
order. Your AI hands Kesl the task, with what it already knows from your chat, as one
**Open in Kesl** link; Kesl does the clicking and answers back.

It follows the open [Agent Skills](https://agentskills.io) format, so it works in Claude,
ChatGPT and any agent that reads skills. Install page: [kesl.ai/skill](https://kesl.ai/skill).

## Install

**Claude Code:**

```
/plugin install kesl --marketplace bcoughlin/kesl-skill
```

**Claude (claude.ai and the desktop app):** under **Customize › Plugins**, choose **Add
marketplace** and paste `bcoughlin/kesl-skill`, then install Kesl. If you don't see that,
download `kesl.zip` from the [latest release](https://github.com/bcoughlin/kesl-skill/releases/latest)
and upload it under **Customize › Skills**. Type `/kesl` to use it.

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

Say what Kesl should do, for example: *"Have Kesl check my boarding time for my Frontier
flight to Salt Lake City in the morning. I'm at Resorts World; when should I call an Uber?"*
You get the request and an Open in Kesl link; tap it on your iPhone. For longer, multi-step
tasks it writes a Kesl runbook instead.

## Versions

An installed skill doesn't update itself. To update, install it again the same way; in ChatGPT, sending the install message again replaces your copy with the newest version.

Each release is tagged `vX.Y.Z`, and the version is in `SKILL.md` (`metadata.version`). What
changed in each one: [CHANGELOG.md](CHANGELOG.md).
