# Elevate Office — changelog

## Build 1.2 — 2026-08-14
- New Training tab: 34 walkthrough videos pulled from the SharePoint Training Videos folder, grouped by topic — Beginner (9), GPS (5), Surface/modelling/cross-sections (3), PMBC/closure/parcel map (5), BCLS & Project Manager (6), General/other (6).
- Each entry links straight to the video (Vidyard, YouTube, Screencast) extracted from the folder's .txt pointer files; entries with a second reference link show it alongside.
- The folder's "obsolete" videos are intentionally excluded so staff aren't learning retired workflows.
- No changes to checklists, tools, or samples.

## Build 1.1 — 2026-08-14
- Samples tab expanded from a stub to the real library: 22 example plans pulled from the SharePoint samples folder, grouped by type — Topos (7), Certificates (4), Sketches (5), FAR (2), Block plans & as-builts (2), Monitoring (2). Legal-plan samples unchanged.
- Each group lists its files and an "open folder" shortcut into SharePoint, so newly filed plans are reachable even before they're named.
- No changes to checklists or tools.

## Build 1.0 — 2026-08-13
First release.
- Checklists: Topographic 2026, Building Location Certificate 2026, New Construction 2026, Property Line Sketch 2026 — content word-for-word from the SharePoint source PDFs. Property Line Sketch is the 2025 sketch checklist updated to 2026 with two items added to the model-space section (control cleanup, point protection), replacing the overwritten 2026 PDF.
- Tick items Yes / N/A; every tick auto-stamps initials + date. Long items show lead phrase with expandable detail (full source wording preserved).
- Section footers auto-sign "Completed by [initials] on [date]" from whoever ticked the items; PM/Finalize sections flagged orange.
- Auto-save to the browser per checklist + job number; in-progress list on the home screen; storage-persist requested.
- Handoffs: "Save to job file" downloads {job}-{type} checklist.json; Import (button or drag-and-drop) restores it exactly. Wording-signature check warns if checklist text changed between save and import. Save button pulses when a checklist is 100% but unexported.
- Print / PDF button produces a paper-style record with checked boxes and stamps.
- Read-only banner when opened in an in-app browser or a context that can't save.
- Keyboard on PC: arrows/J/K move, Y yes, N n/a, C clear, D detail.
- Tools: quadrant bearing ↔ azimuth converter, bearing add/subtract (DMS with carrying, normalized + raw result, chaining), feet ↔ metres, four-way area converter (m² / sq ft / acres / ha), invert calculator (rim in m or ft, depths in m, optional top-of-pipe deduction by size in mm, results in both units, copy-out).
- Samples tab linking SharePoint sample plans + folders; Resources tab with all 21 city GIS viewers from CITY GIS LINKS.xlsx plus Canada Lands and Crown Grants.
- What's-new card, Build number in header.
