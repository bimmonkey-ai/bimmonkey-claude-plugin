# BIM Monkey for Claude

Your firm's Revit library, drawing standards and live Revit, inside Claude.

BIM Monkey is a Revit plugin plus a web app that learns how your firm draws: it reads your permit-ready sets, synthesizes your standards, and applies them while you work. This Claude plugin connects Claude on the web, desktop or phone to that account, and packages the workflows people actually use with it.

## What it adds to Claude

| Skill | Ask Claude… |
|---|---|
| **Permit set QA** | "Check this set against our standards before it goes to intake." |
| **Standards Q&A** | "How do we name RCP sheets?" "What's our callout convention?" |
| **Field reference** | "Show me A2.1 from the Baines project." "Find our deck ledger detail." |
| **Project to-dos** | "Add to the 3421 project: move the W4 tag off the dimension string." |
| **Code reference check** | "Verify the code references on the cover sheet against current sources." |
| **Session log** | "Write up today's session for the daily log / for a case study." |
| **Export from Revit** | "Export G1.0 from the 3421 model to PDF." (needs the project open in Revit at the firm) |

## Setup

1. A BIM Monkey account (free trial at https://bimmonkey.ai). Your firm's API key is under Settings in the web app.
2. Add this plugin in Claude → Customize → Plugins, or in Claude Code:

   ```
   /plugin install bim-monkey --marketplace showme2thebike/bimmonkey-claude-plugin
   ```

   When the connector asks you to authorize, paste the firm's `bm_` key once.
3. For live exports and anything that edits a model, the BIM Monkey Revit plugin must be installed and the project open in Revit: https://bimmonkey.ai/install

## What the connector can and cannot do

- Reads your firm's library, synthesized standards, firm memory, project notes and compliance results.
- Writes project to-dos and firm memory notes.
- Can ask the Revit that is open at the firm to export sheets to PDF. It cannot edit a model from the cloud; model changes happen in Banana Chat inside Revit.
- Data stays with your firm: Enterprise accounts with data residency keep their library in their own database and bucket.

Support: https://bimmonkey.ai/getting-started.html · Privacy: https://bimmonkey.ai/privacy.html · Terms: https://app.bimmonkey.ai/tos
