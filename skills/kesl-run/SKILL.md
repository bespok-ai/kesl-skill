---
name: kesl-run
description: Have Kesl, the browser agent on the user's iPhone, do something on the web for them (check a flight, look something up on a live site, fill in a form, book or order), handed over as one Open in Kesl link with the context from this conversation. Reads kesl.ai/run each time for Kesl's current instructions. Use when the user says "have Kesl...", "ask Kesl", "send this to Kesl", asks for a Kesl runbook, mentions kesl.ai/run, or wants a web task done on their phone.
metadata:
  version: "1.2.1"
  homepage: "https://kesl.ai/skill"
---

# Have Kesl do it

Use this when the user wants Kesl to do something for them, or mentions Kesl or kesl.ai/run.

## First, read kesl.ai/run

Kesl's instructions for AI assistants live at **https://kesl.ai/run.md** (the plain-text version of kesl.ai/run) and change as Kesl does. Every time this skill is used:

1. Get the full text of https://kesl.ai/run.md before writing anything, and follow what it says. It replaces the copy below. Don't rely on memory or a copy read earlier.
   - **Get the whole file, not a summary.** The link format below has to be exact, and some fetch tools (Claude Code's web fetch, for one) return only a summary. If you can run a shell command, use `curl -sL https://kesl.ai/run.md`, which returns the exact text. Otherwise use your web or fetch tool and ask it for the full text.
   - If all you get back is a summary, follow it for what's changed, and take exact formats (the request, the runbook, the link) from the copy below.
2. Do what it says with the context from this conversation, so the user never has to paste kesl.ai/run.
3. Only if you can't open the page (no web access, or it fails to load), use the copy below; it may be out of date.

## Copy of kesl.ai/run, for when the page can't be opened

This copy is kesl.ai/run version 1.2.1, Nov 19, 2026. The page may be newer.

### What Kesl is

Kesl is a web browser on the user's iPhone with a built-in agent. Kesl does the task itself: it opens the sites, signs in, clicks, reads the page, fills in forms, and submits or pays when the task says to. The user types any password or card number themselves. Kesl handles pop-ups, sign-ins, and pages that look different than expected, and it answers back in its own chat. Your job is a clear ask, not every click.

### What to do now

**If you have Kesl's tools** (the Kesl connector: `send_runbook` and `get_result`), use them instead of a link: write the request as below, send it with `send_runbook`, and check back with `get_result`. The task reaches the user's iPhone as a notification, and Kesl's answer comes back to this chat. Only if you don't have them, or a send fails, follow the steps below.

1. Write the task as a short request to Kesl, in plain words, with the context from this conversation that Kesl would otherwise have to ask for (see "Writing the request").
2. Put it in a single code block so it's easy to copy.
3. Below it, give an **Open in Kesl** link (see "The link").
4. Then tell the user what to do next (the "Next steps" text below).

If you don't know which task the user means, ask them in one short question before writing anything.

### Writing the request

Most tasks are one request: a first line saying what to do and what to report back, then the context.

```
Kesl: <what to do, and what to tell me when it's done>
<context: the details from this conversation Kesl needs>
```

- **Say what answer or result the user wants**, not only the task: "tell me when boarding starts and when I should leave", not "check my flight".
- **Include what you know.** The airline, the route, the date, where they are, names, sizes, budgets: anything said in this conversation that saves Kesl a question. Skip what you don't know; Kesl will ask.
- **Name the site if it matters.** For a booking, a flight or an order, the company's own site is usually best ("on frontier.com"). Otherwise let Kesl choose.
- **Leave private details out.** No passwords, card numbers or ID numbers. Write `[ask me]` where one is needed (a confirmation code is fine to include if the user gave it to you).
- **Write the whole task, to the end.** Kesl does what you ask, including a final Submit, Pay or Send. Only if the user wants to check first, add `Stop and ask me before: <that step>`.

#### Longer tasks: a runbook

When the task has several distinct steps on a site, or the user will want to do it again, write it as a runbook instead. Its first line must start with exactly `Kesl runbook:`; that's how Kesl recognizes one and runs it as the plan.

```
Kesl runbook: <one-line goal, in plain words>
Start at: <URL of the site where the task begins>
Ask me for: <details Kesl will need from the user, separated by semicolons>

Steps:
1. <one plain action per step>
2. ...

Done when: <what the user will see when it worked>
```

- Plain steps, one action each ("Open Activities, then Band Camp"), not selectors or code. If you're not sure where something is on the site, describe the goal of the step and let Kesl find it. Most runbooks are 3 to 8 steps.
- Only if the user will do it again (a weekly order, the same form each month), add `Save: yes` and a short code (`Code: lunch-money`: lowercase letters, digits and dashes, under 20 characters). Kesl offers to save it, and `kesl.ai/run?<code>` runs it again with one tap. Otherwise leave both out.

### The link

Give the user a link that opens the request in Kesl:

```
https://kesl.ai/ask?<the whole request, URL-encoded>
```

Encode the text exactly as written, so Kesl receives the same text as the code block: spaces as `+`, line breaks as `%0A`, a real plus sign as `%2B`, and other punctuation percent-encoded as usual. For example, `Kesl: Check my flight` becomes `Kesl%3A+Check+my+flight`. Show it as a tappable link labeled **Open in Kesl**, never as a bare address.

- **The link goes after the code block**, never first: while your reply is still appearing, the link can show as its raw address for a moment, and a screenful of `%20`s looks alarming before the user has seen what it does.
- **Keep the request short** (a few lines, under about 400 characters) so the link stays short. Leave out anything Kesl will find on the site itself.

### Examples

The user, at Resorts World in Las Vegas and flying Frontier to Salt Lake City in the morning, wants to know when to call an Uber:

```
Kesl: Check my Frontier flight from Las Vegas (LAS) to Salt Lake City (SLC) tomorrow morning on frontier.com, and tell me the departure and boarding times, and when to call an Uber.
I'm at Resorts World Las Vegas, about 20 minutes from LAS by car. Confirmation code: [ask me]
```

A longer task, as a runbook:

```
Kesl runbook: Register Jake for summer band camp
Start at: https://www.example-school.org
Ask me for: the parent portal login; Jake's T-shirt size

Steps:
1. Sign in to the parent portal.
2. Open Activities, then find Summer Band Camp.
3. Start registration for Jake.
4. Fill in the form with Jake's details.
5. Submit the registration and pay the fee.

Done when: the site shows a registration confirmation for Jake.
```

### Next steps (tell the user this, in your own words)

- **On your phone:** tap **Open in Kesl**, then tap the button on that page. Or copy the text, open Kesl, and paste it into the agent bar.
- **On a computer:** text or email the link to yourself, then open it on your phone.
- **Don't have Kesl yet?** Get it on your iPhone from kesl.ai/download, then tap the link again.
- Kesl does what the request says, including any Submit or Pay step, so read it before you send it; you type any password or card number yourself.
