---
name: code-reference-check
description: Verify the building and zoning code references on a set (cover sheet code summary, occupancy, construction type, zoning citations) against current sources, and explain what changes if a classification changes. Use when the user asks to "check the code references", "is this citation current", "what occupancy is this", or pastes a code summary.
version: 1.0.0
---

# Code reference check

Treat every citation on the sheet as a claim to be verified, one at a time.

## Steps

1. **Collect the claims.** From the uploaded sheet, `get_sheet_image` of the cover or code summary, or the user's pasted text: the code editions named, each section cited, occupancy group, construction type, sprinkler status, zoning designation and any numeric limits (height, setbacks, lot coverage, FAR).
2. **Verify each against a current source.** Use web search for the adopted code edition and amendments of the named jurisdiction, and the jurisdiction's zoning code for the parcel's zone. Record the source you used for each item. Where the firm has saved jurisdiction rules in `get_firm_memory`, use them and say so.
3. **Classify each item** as: confirmed (section says what the sheet says), outdated (edition or section number changed; give the current one), unconfirmed (could not reach a current source), or wrong (sheet contradicts the source; quote both).
4. **Explain consequences only when asked or when a classification is wrong.** For example what changes in egress, fire separation or sprinklers if the occupancy moves from R-3 to R-2.
5. **Report** as a table: Sheet item · Status · Current source · Note. Then one line on what to change on the sheet.

## Rules

- Never mark something confirmed without a source you actually read in this session. "Unconfirmed" is an acceptable, honest result.
- Jurisdictions amend model codes. The model code section is not enough; check the local adoption.
- Do not give the architect's legal opinion. State what the source says and where.
