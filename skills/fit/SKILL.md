---
name: fit
description: Fit the reply to one screen of the terminal. Use when the user invokes it, with a message to answer or with nothing to cut the previous reply.
license: CC0-1.0
compatibility: Requires a terminal with a real TTY and python3. The leading placeholder needs a client that substitutes skill arguments into the body; on clients that do not, pass the message as ordinary text after the skill name.
argument-hint: "[a message, or nothing]"
---

$ARGUMENTS

***

Everything above the rule is an ordinary user message. Answer it exactly as you would have if it had been typed on its own. It does not become a request for a summary, an overview, or a shorter kind of answer — only the length of the reply is constrained.

If there is nothing above the rule, the target is the previous assistant message. The reply is that message, cut to fit. Answer nothing anew, and rewrite nothing that survives the cut.

You cannot count your own output while writing it, and the count that matters is not newlines — it is rendered lines after wrapping at the real width. So the reply is drafted, measured, and cut before any of it reaches the screen.

## Procedure

1. Write the whole reply to a file in a temporary directory. Nothing goes to the screen yet.
2. Run `scripts/check <file>`, resolved against this skill's base directory.
3. On `OVER by N lines`, cut at least N lines from the file and run it again. Repeat until `OK`.
4. On `OK`, reproduce the file verbatim as the reply.
5. On `NO TERMINAL`, there is nothing to fit. Reply from the file as it stands.

## Rules

- **Do not aim at a length.** A target is something to miss. The script measures; you cut and re-run.
- **Cut, do not compress.** Drop the least load-bearing content whole. Hedging, abbreviating, and dropping qualifiers buy a few columns and cost accuracy.
- **Do not edit while copying.** No typo fixes, no rewording, no collapsing blank lines. The checked draft is the reply; anything changed after the check was never measured.
- **Say nothing about the process.** Not the draft path, not the rounds, not the measurements. The reply is the answer alone.
