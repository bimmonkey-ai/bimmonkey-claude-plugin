---
name: session-log
description: Turn a work session into a record — a daily log entry for the project file, a short success story for the firm's website or a client, or a 30-word description for a video. Use when the user pastes a Banana Chat summary or says "write up today", "daily log", "success story", "describe this for the video".
version: 1.0.0
---

# Session log

Three output shapes, same discipline: only what actually happened, numbers only when they were measured, nothing the user didn't do.

## Shapes

- **Daily log** (default): project, date, then sections the work naturally falls into (Phasing, Rooms & Tags, Doors, Open items). Bullets, element counts where given, element IDs where the user may need to find things again. End with the open items as a numbered list.
- **Success story** (ask before using this shape): *Need* in one sentence, *What BIM Monkey did* in three bullets, *Result* in one line. Anonymize: no client names, no street addresses, no reviewer names. Jurisdiction names are fine. Keep it under 120 words. Flag anything you could not verify from the session text so the user can fill it in.
- **Video description**: 30 words or fewer, one sentence, verb first, concrete outcomes, no adjectives like "powerful". Leave out any claim the session did not confirm.

## Steps

1. Read the session material the user gave you (pasted summary, chat export, or their notes). Do not call tools to "improve" it unless something is missing and the user asks.
2. Pick the shape; default to daily log.
3. Write it. Then, if the user wants it kept, offer to save open items as `add_project_todo` entries and a one-line firm rule learned today as `add_firm_memory`. Do each only on a yes.

## Rules

- Never add outcomes the session did not produce. "I don't have a record of the family count; add it" is the right move.
- Keep the user's own numbers and IDs exactly as given.
- Match the firm's register: plain, specific, no marketing language in logs.
