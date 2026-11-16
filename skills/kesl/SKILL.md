---
name: kesl
description: Turn a task into a Kesl runbook, a short plan the Kesl browser carries out on the user's iPhone, with an Open in Kesl link. Use when the user asks for a Kesl runbook, says "send this to Kesl", "have Kesl do it", "make this something Kesl can run", or wants a web task (booking, ordering, a form, a check-in) done on their phone by Kesl.
metadata:
  version: "1.0.0"
  homepage: "https://kesl.ai/skill"
---

# Kesl runbooks

Use this when the user wants Kesl to do a task for them. Write the runbook from what you've discussed, following the steps below.

## What Kesl is

Kesl is a web browser on the user's iPhone with a built-in agent. Kesl does the task itself: it opens the sites, clicks, fills in forms, and does each step as written, submitting or paying when a step says to. The user types any password or card number themselves. Kesl handles pop-ups, sign-ins, and pages that look different than expected. Your job is the plan, not every click.

When a runbook reaches Kesl, Kesl does the task. If the runbook says `Save: yes`, Kesl offers to save it afterward; a saved runbook gets a short code, and the user can run it again any time with one link. Most runbooks are one-time tasks (`Save: no`), and Kesl just does them.

## What to do now

1. Write a runbook for the task from this conversation, in the format below.
2. Put the runbook in a single code block so it's easy to copy.
3. Below it, give an **Open in Kesl** link (see "The link" below).
4. Then tell the user what to do next (the "Next steps" text below).

If you don't know which task the user means, ask them in one short question before writing anything.

## Runbook format

```
Kesl runbook: <one-line goal, in plain words>
Save: <yes if the user will run this again; no for a one-time task>
Code: <short code, like las-slc; only with Save: yes>
Start at: <URL of the site where the task begins>
Ask me for: <details Kesl will need from the user, separated by semicolons>

Steps:
1. <one plain action per step>
2. ...

Done when: <what the user will see when it worked>
```

The first line must start with exactly `Kesl runbook:`. That's how Kesl recognizes it.

## Rules for writing it

- **Plain steps, one action each.** "Open Activities, then Band Camp." Not CSS selectors, not code.
- **Don't guess at the page.** If you're not sure where something is on the site, describe the goal of the step ("find the registration form for band camp") and let Kesl find it.
- **Save: yes or no.** Say yes only for something the user will do again (a weekly order, a recurring check-in, the same form each month). A task for today is `Save: no`, and needs no code.
- **A short code** (only with `Save: yes`). Lowercase letters, digits and dashes, under 20 characters, easy to type: `las-slc`, `band-camp`, `lunch-money`.
- **Leave private details out.** Don't write passwords, card numbers, or ID numbers into the runbook. List what's needed under "Ask me for", or write `[ask me]` in the step; Kesl will ask the user or fill it in from what it already knows.
- **Write the whole task, to the end.** Kesl does every step as written, including the final Submit, Pay or Send. Don't add a stop the user didn't ask for. Only if they asked Kesl to check with them first, add a line `Stop and ask me before: <that step>` after the steps.
- **Keep it short.** Most runbooks are 3 to 8 steps.

## The link

Give the user a link that opens the runbook in Kesl:

```
https://kesl.ai/ask?<the whole runbook, URL-encoded>
```

Encode the runbook text exactly as written, including the line breaks (`%0A`), so Kesl receives the same text as the code block. Show it as a tappable link labeled **Open in Kesl**.

For a quick one-time task that doesn't need a runbook, you can skip the runbook and link the request itself: `https://kesl.ai/ask?Book%20a%20table%20for%204%20at%207pm`.

## Example

```
Kesl runbook: Register Jake for summer band camp
Save: no
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

## Next steps (tell the user this, in your own words)

- **On your phone:** tap **Open in Kesl**, then tap the button on that page. Or copy the runbook, open Kesl, and paste it into the agent bar.
- **On a computer:** text or email the link to yourself, then open it on your phone.
- **Don't have Kesl yet?** Get it on your iPhone from kesl.ai/download, then tap the link again.
- Kesl does the steps as written, including any Submit or Pay step in it, so read the runbook before you send it; you type any password or card number yourself. If it says `Save: yes`, Kesl offers to save it after, and `kesl.ai/run?<code>` runs it again with one tap. You can save a one-time runbook too, by asking Kesl to.
