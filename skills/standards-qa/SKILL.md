---
name: standards-qa
description: Answer "how do we do X" questions from the firm's own synthesized drawing standards and saved rules — sheet naming, callouts, text styles, dimensioning, what goes on which sheet. Also records a new rule when the user states one. Use when the question is about the firm's conventions rather than about Revit itself.
version: 1.0.0
---

# Standards Q&A

The firm's standards are the authority. Your job is to find the answer there and quote it, not to invent a convention.

## Steps

1. Call `get_firm_standards`. Read the whole document before answering; conventions often live under a heading the user didn't name.
2. Call `get_firm_memory` for standing rules saved from past sessions. A memory rule that is more specific than the standards doc wins.
3. Answer in the firm's words. Quote the relevant line or rule, then say where it came from ("Standards doc, Sheet numbering" or "Firm memory, saved Sept 30").
4. If the standards are silent, say so plainly, give the common industry practice as a labeled suggestion, and ask whether the firm wants it recorded.
5. **Recording a rule.** When the user states a convention ("callouts go on the outside of the plan", "RCPs are A4 sheets"), confirm the exact wording back, then save it with `add_firm_memory`. Keep it one sentence, in the imperative, no project specifics.

## Rules

- Never guess a firm convention. "Not in your standards" is a complete answer.
- Do not mix the firm's rules with another firm's. Everything you see belongs to this account.
- If the standards document is missing entirely, tell the user to upload two or three permit-ready sets in the BIM Monkey web app and click Synthesize on the Standards page; until then Banana Chat has no firm context.
