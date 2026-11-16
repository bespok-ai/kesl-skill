# Changelog

The Kesl skill: what changed in each version. The newest version is the first heading;
`build_pages.py` reads it and stamps it into `SKILL.md`, and refuses to build when the skill
text changed but this file didn't get a new version. Versions follow semver:

- **major**: a runbook written by the old skill no longer works, or the format changes shape;
- **minor**: something new the skill can write (a field, a kind of task);
- **patch**: wording, examples or fixes that don't change what a runbook can contain.

Published copies: github.com/bcoughlin/kesl-skill (tagged `vX.Y.Z`, with kesl.zip on each
release) and kesl.ai/skill.

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
