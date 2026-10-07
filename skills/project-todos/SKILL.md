---
name: project-todos
description: Capture and review drafting tasks on a BIM Monkey project — punch items from a site walk, redline notes, "remind the model to…" — so they show up in Banana Chat the next time the project is open in Revit. Use when the user says "add to the project", "note for the model", "what's open on this project", or dictates a list of fixes.
version: 1.0.0
---

# Project to-dos

Turn what the user says into tasks a drafter can act on in Revit, attached to the right project.

## Steps

1. **Resolve the project.** Call `get_project` or `query_library` with the name the user used. If it returns candidates, ask which. Never attach a task to a guessed project.
2. **Write tasks that can be acted on.** One task per item, imperative, with the sheet or view and the element when known: `A2.1 — move the W4 tag off the dimension string at grid C`. Keep each under two lines. Split "and" items into separate tasks.
3. **Confirm before saving** when the list is long or the wording is ambiguous: read the tasks back once, then call `add_project_todo` for each.
4. **Review.** For "what's open", call `get_project_todos` (optionally for one project) and present them grouped by project, oldest first.

## Rules

- Tasks are for the project, not personal reminders. If it isn't about a building project, say so and don't save it.
- Don't invent element IDs or sheet numbers. If the user doesn't know the sheet, leave it out rather than guess.
- After saving, tell the user where it lands: "Banana Chat will list this under open to-dos when the project is open in Revit."
