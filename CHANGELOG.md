# Elevate Office — changelog

## Build 1.11.1 — 2026-09-10
- Fix: dragging a file anywhere on the Points tab now goes to the Points loader. The app-wide checklist import was grabbing every drop, so a dragged .msz showed "Drop checklist file to import" and never reached the Points tab (Choose file worked; drag didn't). The overlay now says "Drop points file or drawing package" on Points and routes accordingly; on Checklists it behaves as before.
- Points: the package banner's button is now "Points file — uncorrected" with a note that it's exactly what the database holds, no fixes applied — the quick path when an .msz is dropped just to get a points file. Above the fixes, Untick all / Tick all fixes controls: untick everything and the full cleaned file comes out uncorrected too.
- Wording: the .mbz note now says it's the automatic backup — a different snapshot from the .msz whose date should be checked — rather than assuming it's older (a background save can be newer than the last manual save). Legacy .msd projects get a clear message to open once in MicroSurvey, which converts them to .msz.

## Build 1.11 — 2026-09-10
- **Points from a drawing package.** Drop a MicroSurvey `.msz` (project zip) or `.mbz` (backup zip) onto the Points tab and the points are read straight from the coordinate database inside it (`db_coord.dbf`) — no CAD needed. Verified byte-identical against a points file exported from MicroSurvey CAD the same day. The package date is shown, a `.mbz` is flagged as a backup that may be older than the `.msz`, and a share-conflict copy of the database is reported if present (the primary is used). The points feed the normal pipeline — cleanup, extraction, scaling — or download directly as a points file. A bare `db_coord.dbf` is accepted too. Zero libraries: the zip is read with the browser's built-in decompression and dBase is parsed directly.
- Scale: one factor field replaces the two-button mode. Below 1 reads as ground → grid (file suffixed -GRID), above 1 as grid → ground (-GROUND); a 1/x button flips between them. A booked monument carrying a scale factor in its description (e.g. `89H5014booked sf-0.99960238`) is auto-detected and offered as the scale point with the factor pre-filled and elevations left untouched — one tap, no retyping. Direction label and download state now refresh as you type; checkbox hint spacing fixed.
- Combined scale factor: the geoid separation is no longer pre-filled with a regional guess. Enter the value from your GNSS export's Geoid Separation column, the mascot listing, or NRCan — the tool won't compute without it, and with it the result matches the export to 8 decimals.

## Build 1.10 — 2026-09-08
- Points tab: **Scale about a point**. Three modes — metres → feet (× 3.280839895), feet → metres (× 0.3048), and custom: either paste a combined scale factor for grid → ground (the tool applies 1/CSF and shows the multiplier before you commit) or type a factor directly.
- Scale point: a point number from the file — SCPT / SCALE PT / SCALE POINT descriptions are auto-proposed — confirmed with its N, E, Z, and description echoed back; or manual N/E/Z entry as a fallback (Z defaults to 0). Nothing scales until a base is confirmed.
- N and E scale about the scale point (it keeps its coordinates). Elevations scale about zero by the same factor on unit conversions and are left untouched on custom / grid → ground scaling (toggle either way). If the scale point's booked elevation isn't zero the tool says so rather than scaling Z about it.
- Output written at the input's decimal precision with descriptions from the cleaned state; point numbers, delimiter, spacing, and line endings otherwise byte-identical. Files suffixed -FT, -M, -GROUND, or -SCALED; a Scale log records mode, base point, factor, and elevation treatment.

## Build 1.9 — 2026-09-02
- The Cleanup tab is now **Points** — one drop of the exported PNEZD file yields every deliverable. Two new extracts join the download row:
- **Control + calc file**: every point whose code the 2026 automap places on the CONTROL layer (OCM, OCNT, OCN, OIP/OIPB/OIPT, OSPK, OMON, OMAG, ORBR, IP, LP, CP, MON, RP and the rest of the found/set-monument family — 37 keys, derived from the automap itself) plus calc points: numbers 1–99, CALC descriptions, and blank descriptions. For carrying a topo forward into a legal file.
- **Client file**: everything else, using the cleaned descriptions — control, calc, and check shots stripped.
- Check shots drop from both extracts: any CHK token, the BS/BSCHK/OCL check family, STK_ re-shot IDs, and leading-point-number descriptions the review identifies as check shots ("1003 OSPK"). Not needed for topo-to-legal or for the client.
- The split (control · calc · deliverable · check shots dropped) shows above the extract buttons and is recorded in the change log. Extracts cover the whole file regardless of focus; formatting, numbering, and coordinates are byte-identical as always.

## Build 1.8 — 2026-09-02
- Comments now show in red — in the app and in the PDF — so notes like "Reverse. See notes" jump out instead of blending into the item text. The bold stamps from 1.7.2 are unchanged; embedded data untouched.
- In-progress list managed: shows the five most recently worked checklists (anything unsaved always stays visible) with a Show all expander; every row has a ✕ to remove it from this computer — a calm confirm when it's saved to the job file, a strong warning when the browser copy is the only copy. Checklists saved to the job file and untouched for 30 days are tidied away automatically, with a one-line note when it happens; the job-file PDFs remain the record and re-import brings anything back.
- Invert calculator: pipe size is entered in metres like every other number — a 300 mm culvert is 0.3, a 150 is 0.15. Values over 3 get a gentle "this field is metres" nudge.
- Resources: Training videos group linking the SharePoint library and its beginner, GPS items, Automap, and BCLS + project manager sections.
- Note: the toast-shield item from the queue doesn't apply to Elevate Office (no toast element exists in this app); it remains a Field Notes fix.

## Build 1.7.2 — 2026-08-31
- Fix: the "unsaved to job file" flag no longer comes back after a save when you merely reopen the checklist, go back to the library, close the tab, or take an update-banner refresh. The saved record's "updated" timestamp now moves only on real changes (ticks, check stamps, comments, sheet numbers, pages added/removed, job number) — not on every save-to-browser. Anything genuinely changed after an export still flags correctly.
- PDF checklists: the [YES] / [N/A] / [CHK] stamps now print bold black so the answers stand out, with initials and date slightly quieter beside them. Comments print darker and a step larger. Rendering only — the embedded data is unchanged, so PDFs from any build import identically.
- Note: checklists exported on older builds may still show the flag once; the next Save PDF or JSON export on 1.7.2 clears it for good.

## Build 1.7 — 2026-08-24
- New: Code cleanup, its own tab. Drop an exported PNEZD points file (.txt/.csv/.asc — the raw RW5 is refused) and every description validates against the current ELEV-AUTOMAP-2026 metric + imperial key lists. Point numbers, coordinates, and elevations are never touched; outputs preserve the original delimiter, spacing, and line endings byte for byte outside the accepted changes.
- Pre-ticked fixes for confirmed miscodes: OIP B / OIP T / OIP BASE / OIP BENT → OIPB/OIPT (OIPT held on a known-pending list until the 2027 automap publishes it), TCONN → TCON, SPK → OSPK, codes glued to their numbers (OCNT8221 → OCNT 8221), underscores → spaces in descriptions only, trailing whitespace, and THCED/THDEC → TH CED / TH DEC. Every fix is per-point untickable.
- Drip lines booked in centimetres (third token over 25) normalize to metres on every run. When the file has trees, a metric/imperial question appears; imperial converts tree diameters cm÷30.48 and drip lines m×3.28084 to feet, 2 decimals, trailing flags like MS preserved. The change log records the answer.
- Unticked suggestions: STUMP → TSTUMP, DOOR SIL → SILL, CONWW → WWCON, BLOCK WALL → RTB, and leading-point-number descriptions (e.g. "1003 OSPK") → CHK check-shot form.
- Add your own fix: one-off find/replace rules with live match preview before committing, whole-token matching by default, optional point-range scope. Rules die with the file.
- Point-population chips summarize the file's numbering blocks (with blank counts) and let you exclude any block — issued search points, office COGO ranges — from cleanup entirely; exclusions are recorded in the change log.
- Codes outside the automap are listed once, collapsed, as information only — legal-search vocabulary, control notes, and combined codes like BT-HWM are never flagged as wrong or altered. Blank descriptions pass through silently with a count in the summary and log.
- Three outputs always: full cleaned file, corrections-only file, and a change log tagging every change as fix, suggestion, or manual rule.

## Build 1.6 — 2026-08-21
- New tool: Calculator — a single expression line with add, subtract, multiply, divide, and parentheses. Paste numbers with commas, × and ÷ both work, the result shows live, and Enter keeps the line on a running tape; tape results can be copied or clicked back into the next expression so chained work never re-keys numbers.
- New tool: Combined scale factor — enter northing, easting, orthometric elevation, and geoid separation (pre-filled −18.2 m for the Lower Mainland, editable) from a corrected network RTK observation; the tool derives ellipsoidal height and computes grid, elevation, and combined factors to 8 decimals on GRS80, matching NRCan/mascot output. Copy results carries the inputs, all three factors, and the RTK-basis statement into the calc notes. A standing note on the tool restricts use to corrected dual-frequency network RTK observations or better.
- Resources: workflow note added for bringing vector architectural PDFs into MicroSurvey with PDFIMPORT — scale by reference off a labelled dimension, verify against a second, keep imported linework as reference-only on its own layers, and treat a PDFIMPORT that returns nothing as the signal the PDF is a scan.
- Fix: the update check now skips quietly when fetch is unavailable (file:// testing).

## Build 1.5 — 2026-08-18
- Four new checklists, transcribed from the office PDFs on SharePoint: **Preliminary Strata** (Page 1 + Units), **Final Strata** (Page 1 with closure and PMBC, Units, Cross sections, optional Building foundations), **Legal Plan 2026**, and **Ex. Plan 2025**. Duplicated "Unfreeze" items in the two PMBC sections were de-duplicated, a doubled word in the Final Units source was corrected, and "preffered" was corrected to "preferred" in both legal lists; the source PDFs remain the wording of record.
- Dual-check system on both strata checklists: each item takes a first pass (Yes/N/A) plus a separate Chk stamp. The Chk button unlocks only after the first pass, warns when the same initials try to do both, and any change to the first pass clears the check. Section footers show both names; both passes travel in JSON, PDF, and print.
- Strata Units, Cross sections, and Foundations pages can be added and removed per job, each with its own sheet-number field. Removing a page asks before deleting its ticks; mandatory pages keep a minimum of one. Pages, sheet numbers, and their ticks travel in all exports.
- Per-item comments on every checklist (✎): independent of tick state, don't affect the progress bar, ride along in JSON and PDF, and print as indented notes.
- Proration: once a side has a factor (derived or manual), an apply strip takes intermediate plan calls and shows each prorated value plus a cumulative chainage column. Copy results carries the applied block, labelled with the factor.
- Proration: per-side m/ft toggle for plan calls (exact 0.3048 conversion). The field box and every output stay in metres; Copy results shows the full chain per call (ft → m plan → m prorated) and notes the conversion.
- Invert calculator: direction/pipe column removed — rows are just depth → invert, numbered in Copy results; the field sketch remains the record of which invert is which.
- Date cell removed from the checklist title block — per-item stamps carry the dates.
- Update awareness: the app checks the live changelog on open, on tab focus, and every 30 minutes, and shows a "Build X is available — Refresh" bar when a newer build has shipped. Refreshing is safe mid-checklist (every tick is already persisted); "later" snoozes it for about half an hour. Browsers with the app closed simply pick the new build up on next launch.

## Build 1.4.1 — 2026-08-17
- Fix: the "unsaved to job file" flag now clears properly after Save PDF or JSON export. A timestamp race meant every export immediately re-flagged itself as unsaved, so the daily reminder and orange badge never went away.
- Fix: importing a saved file (PDF or JSON) no longer shows the checklist as unsaved — it only flags again once you make a new change.

## Build 1.4 — 2026-08-17
- Save PDF to job file: the app now generates its own checklist PDF — checked boxes, N/A crosses, initials + date stamps, section signoffs — with the full checklist state embedded invisibly in the same file. One artifact serves both workflows: anyone can read it as a normal PDF, and importing it into the app restores every tick to continue (e.g. PM Checks after the drafter's pass). Import accepts app-made PDFs and JSON alike, by button or drag-and-drop; PDFs from other sources are declined with a clear message. JSON export stays available; Print remains for quick paper copies.
- Daily reminder: opening the app lists any checklists with changes not yet saved to the job file (job #, progress, last-worked date, click to open), dismissible until tomorrow. The in-progress list also flags them with an orange "unsaved to job file" badge.
- Samples: legal plans filled out and grouped — Postings, Reference plans (road closure, sec 107 dedicate road, sec 100(1)(a) old area), SRW (0.5 SRW Surrey, volumetric), Subdivisions, Ex. plans, and Strata (townhouse + condo unit samples, Form V duplex) — each with an open-folder shortcut.
- Resources: GeoNetBC (geodetic control) added under Provincial/federal; new Company reference group with the past-jobs Google My Maps (read-only viewer link).

## Build 1.3 — 2026-08-14
- New tool: Proration. Per-side cards named as you like (NORTH PL...); enter multiple plan (record) calls — Enter on the last row adds another — against one measured field distance. Factor = field ÷ Σ plan derives live at 8 decimals with full internal precision; every call shows its prorated value at 3 decimals and a Σ check confirms the prorated calls rebuild the field distance. Type a factor directly (Helmerts result, combined scale) to switch the card to manual mode: a blue tag shows, the field box becomes an output showing the implied distance, and Copy results labels each side (derived) or (manual) for the calc notes. Add/remove sides freely while working a calc.
- New tool: Absolute accuracy (95%). One row per point/monument: enter σN and σE off the transformed-coordinates report; accuracy = 1.96 × √(σN² + σE²) shows with the combined σ beside it. The governing (largest) point is highlighted in orange — that's the accuracy-statement value — and Copy results outputs the table with the confidence basis noted (horizontal, 95%, k=1.96).
- No changes to checklists, samples, or training.

## Build 1.2 — 2026-08-14
- New Training tab: 34 walkthrough videos pulled from the SharePoint Training Videos folder, grouped by topic — Beginner (9), GPS (5), Surface/modelling/cross-sections (3), PMBC/closure/parcel map (5), BCLS & Project Manager (6), General/other (6).
- Each entry links straight to the video (Vidyard, YouTube, Screencast) extracted from the folder's .txt pointer files; entries with a second reference link show it alongside.
- The folder's "obsolete" videos are intentionally excluded so staff aren't learning retired workflows.
- New tool: feet-inches → decimal feet + metres. Type a dimension as written on an architectural plan (12' 6 1/2", 12-6, 6 1/2" inches-only, or a bare number for feet) and get both decimal feet and metres for CAD entry. One direction only, by design.
- No changes to checklists or samples.

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
<!-- redeploy -->
