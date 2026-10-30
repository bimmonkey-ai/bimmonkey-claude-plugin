---
name: field-reference
description: Pull a sheet, detail or project fact from the firm's library on demand — on a site visit, in a meeting, or while drafting. Use when the user names a sheet number, a project, or a detail ("show me A2.1", "find our deck ledger detail", "what sheets does the Harbor House set have").
version: 1.0.0
---

# Field reference

Fast lookups from the firm's library. Short answers, the actual drawing when there is one.

## Steps

1. **Project first.** If the user names a project, call `get_project` with that name. Names in the library are whatever was typed at upload; if the tool returns candidates instead of a match, show them and ask which one. Use `query_library` when they only half-remember.
2. **Sheet.** For a sheet number, call `get_sheet_image` with the project and sheet number. Present the image; add one line on what the sheet is and the date on its title block if visible.
3. **Detail.** For a detail by name or type ("deck ledger", "window head at siding"), call `search_details`. Return the best two or three with project and sheet so the user can open the right one.
4. **Fact.** For "how many sheets", "what's the parcel", "which building type", answer from `get_project` and the sheet's own title-block text.

## Rules

- Say which project and which sheet the image came from, every time.
- The library holds the set as it was uploaded. If the user needs the current state of a live model, offer `export_sheet_pdf` (needs the project open in Revit at the firm) rather than passing off the library copy as current.
- Keep answers to what was asked. Do not review or critique the sheet unless asked; that is the permit-set-qa skill.
