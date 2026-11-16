# Changelog

The Kesl skill: what changed in each version. The newest version is the first heading;
`build_pages.py` reads it and stamps it into `SKILL.md`, and refuses to build when the skill
text changed but this file didn't get a new version. Versions follow semver:

- **major**: a runbook written by the old skill no longer works, or the format changes shape;
- **minor**: something new the skill can write (a field, a kind of task);
- **patch**: wording, examples or fixes that don't change what a runbook can contain.

Published copies: github.com/bcoughlin/kesl-skill (tagged `vX.Y.Z`, with kesl.zip on each
release) and kesl.ai/skill.

## [1.0.0] - 2026-11-16

First public version, on GitHub and in the skill directories.

- Turns a task into a Kesl runbook: a short plan in a `Kesl runbook:` code block, an
  **Open in Kesl** link that hands it to the Kesl app on the user's iPhone, and next steps.
- `Save: yes` makes a runbook Kesl offers to keep and rerun from a short code; most runbooks
  are one-time (`Save: no`).
- Works in Claude (type `/kesl`) and ChatGPT Work (type `@kesl`), or any AI that reads Agent
  Skills. The same text as kesl.ai/run, which the skill replaces pasting.
- First served from kesl.ai/skill on Nov 14, 2026 (unversioned, WD-368).
