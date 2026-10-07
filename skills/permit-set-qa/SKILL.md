---
name: permit-set-qa
description: Review a drawing set (uploaded PDF or sheets from the firm library) against the firm's own drawing standards and the jurisdiction's intake checklist before it goes to permit. Use when the user says "QA this set", "check before permit", "what would a plan reviewer flag", or uploads a submittal PDF.
version: 1.0.0
---

# Permit set QA

You are reviewing a set the way the firm's most careful principal would, the day before it goes to intake. Be specific: sheet number, location on the sheet, what is wrong, what the standard says.

## Steps

1. **Get the firm's standards first.** Call `get_firm_standards`. If it returns nothing, say so and review against general practice only, flagged as such. Also call `get_firm_memory` for standing rules the firm has saved.
2. **Get the set.** If the user uploaded a PDF, read it page by page. If they named a project, call `get_project` for the sheet list and `get_sheet_image` for the sheets that matter most: cover, site plan, code summary, floor plans. Do not pull every sheet; ask which ones if the set is large.
3. **Check, in this order:**
   - Cover sheet: project name, address, parcel, scope of work filled in, sheet index matches the actual sheets, code summary present and current.
   - Sheet-level: titles unique, numbers follow the firm's numbering, north arrow, scale stated and consistent with the firm's standard for that sheet type, placeholder text ("XXX", "TBD", template notes) still present.
   - Site plan against the jurisdiction's basic site plan checklist if the user names the jurisdiction (ask once if they don't): property lines with dimensions, setbacks, overhangs with dimensions, existing vs proposed, trees, decks and porches, area figures that match the lot coverage block.
   - Consistency: areas on the cover vs the area schedule, sheet references that point at sheets that exist, detail callouts that land on a detail.
   - Firm standards: anything that contradicts `get_firm_standards` or a saved memory rule.
4. **Report** as a short fix list ordered by what a reviewer would reject first, then what is merely untidy. One line per item: `A1.01 — lot coverage block says 1,085 SF; roof footprint note says 1,288 SF; explain or reconcile.`
5. **Offer to save the list** as project to-dos with `add_project_todo`, one per item, so it shows up in Revit. Only do it when the user says yes.

## Rules

- Never claim a code requirement you have not verified. Say "verify" for anything that depends on the jurisdiction's current adoption.
- Library images can be older than the model. If the user is working from a live set, ask them to export the sheets from Revit (`export_sheet_pdf`) or upload the PDF rather than relying on the library copy.
- Do not rewrite drawings or propose redesigns. This is a QA pass.
