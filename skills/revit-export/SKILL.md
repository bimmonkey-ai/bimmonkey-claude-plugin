---
name: revit-export
description: Get a true, current PDF of one or more sheets from the Revit model that is open at the firm right now, via the export_sheet_pdf tool. Use when the user asks to "export", "send me the current G1.0", "I need the real sheet, not the library copy", or needs a file to issue or upload.
version: 1.0.0
---

# Export from live Revit

`export_sheet_pdf` asks the Revit running at the firm to export sheets and returns download links. It only works when someone has that project open in Revit with the BIM Monkey panel up; otherwise the job waits up to an hour.

## Steps

1. **Find the sheet numbers.** If the user gave them, use them exactly as on the title block (`G1.0`, not `G1`). Otherwise call `get_project` to list the sheets and confirm.
2. **Use the project's file name.** The job is matched against the title of the document open in Revit, which is the file name. If the library name and the file name differ, ask the user what the file is called, or try the library name and fall back.
3. Call `export_sheet_pdf` with `projectName` and `sheetNumbers`. Keep the default wait. Tell the user you're waiting on Revit.
4. **Read the result.**
   - `done`: give the links, one per sheet, and say they expire in 24 hours. Revit 2026 exports one PDF per sheet.
   - `pending`: say that nobody has the project open with the panel up (or the document title didn't match), keep the `jobId`, and offer to check again with `get_revit_job` once they've opened it.
   - `error`: report the message and the failed sheets. "No sheet with this number" means the number isn't in that document; list what is.
5. If the user needs the file somewhere (Drive, email), hand them the link; you cannot upload it for them unless another connector lets you fetch URLs.

## Rules

- This tool never edits the model. Anything that changes drawings happens in Banana Chat inside Revit.
- Don't re-queue the same export repeatedly while one is pending; check the existing job with `get_revit_job`.
- The library copy from `get_sheet_image` may be stale; say which you are giving the user.
