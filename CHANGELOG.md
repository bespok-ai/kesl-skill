# Changelog

The Kesl skill: what changed in each version. The newest version is the first heading;
`build_pages.py` reads it and stamps it into `SKILL.md`, and refuses to build when the skill
text changed but this file didn't get a new version. Versions follow semver:

- **major**: a runbook written by the old skill no longer works, or the format changes shape;
- **minor**: something new the skill can write (a field, a kind of task);
- **patch**: wording, examples or fixes that don't change what a runbook can contain.

Published copies: github.com/kesl-ai/kesl-skill (tagged `vX.Y.Z`, with kesl-run.zip on each
release) and kesl.ai/skill.

## [1.2.1] - 2026-11-19

The skill now reads kesl.ai/run every time instead of carrying its own instructions. Brad:
"All I really want the skill to do is not make me have to repeat kesl.ai/run, but it should
also go and look at kesl.ai/run every time someone mentions it. So basically the skill is just
basically awareness to use Kesl."

- First step: open https://kesl.ai/run.md and follow it. A change to kesl.ai/run now reaches
  everyone who installed the skill, with no reinstall.
- The old instructions stay below as a fallback copy, used only when the page can't be opened.
- Also fires when the user mentions kesl.ai/run.
- Renamed `kesl-run`: type `/kesl-run` in Claude or `@kesl-run` in ChatGPT, and the download is
  `kesl-run.zip`. Brad: "just /kesl probably isn't descriptive enough. Maybe like /kesl-run
  would be nicer." It matches kesl.ai/run, the page the skill reads.
- kesl.ai/run (and so the fallback copy) now says to use the Kesl connector's tools when the AI
  has them, and the Open in Kesl link only when it doesn't. Brad agreed the rule belongs on
  kesl.ai/run, not in the skill, so it reaches everyone without a reinstall.
- kesl.ai/run now has its own version (run/CHANGELOG.md). The fallback copy says which
  version it is, and the skill's version changes only when the skill's own wording does, not
  when kesl.ai/run changes.
- Gets the whole page, not a summary: `curl -sL https://kesl.ai/run.md` where the AI can run a
  shell command, since Claude Code's web fetch returns only a summary of it; with only a
  summary, exact formats come from the bundled copy. Brad: "Normally we paste kesl.ai/run.md
  directly... that always works so that it gets the full context."
- The public repo moved to github.com/kesl-ai/kesl-skill (the old bespok-ai address redirects).
- Requests, runbooks and links are unchanged.

## [1.2.0] - 2026-11-16

"Have Kesl do it" first, runbooks second, and shorter links. Brad: "less about repeatable
runbooks and more about have kesl do something, eg have kesl check my boarding time for the
frontier flight from las to slc in the morning. im at resorts world, need to know when to
call uber"; then, after trying it in ChatGPT on his iPhone, "spitting out the crazy long url
looks scary" and "cant kesl process + instead of url encoded spaces?"

- The default is now a short request (`Kesl: <what to do and what to tell me>` plus the
  context from the conversation), opened with the same Open in Kesl link.
- The request says what answer the user wants, carries what the AI already knows (route,
  date, where they are), and names the company's own site when it matters.
- Runbooks (`Kesl runbook:`) are for longer, multi-step tasks; `Save:` and `Code:` appear
  only for tasks the user will repeat, instead of on every runbook.
- The link: spaces as `+` instead of `%20` (about a third shorter; kesl.ai/ask already
  reads `+` as a space), always after the code block and never as a bare address, with
  requests kept under about 400 characters.
- New example: the Frontier boarding-time check. Description and title reworded; it
  triggers on "have Kesl…" and "ask Kesl" as well as "Kesl runbook".
- Old runbooks and old `%20` links still work unchanged.

## [1.0.0] - 2026-11-16

First public version, on GitHub and in the skill directories.

- Turns a task into a Kesl runbook: a short plan in a `Kesl runbook:` code block, an
  **Open in Kesl** link that hands it to the Kesl app on the user's iPhone, and next steps.
- `Save: yes` makes a runbook Kesl offers to keep and rerun from a short code; most runbooks
  are one-time (`Save: no`).
- Works in Claude (type `/kesl`) and ChatGPT Work (type `@kesl`), or any AI that reads Agent
  Skills. The same text as kesl.ai/run, which the skill replaces pasting.
- First served from kesl.ai/skill on Nov 14, 2026 (unversioned, WD-368).
