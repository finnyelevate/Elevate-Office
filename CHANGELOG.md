# Elevate Office — changelog

## Build 1.46.1 — 2026-11-24
One fix from the first look at 1.46.0.
- **PM › Job map: destroyed monuments were shown (fix).** Every monument in the province's list was drawn as a green triangle, including the ones recorded as destroyed (around Surrey and Langley, more than a third of them). Now:
  - **Green** = published geodetic control monument (the province's "GPS" and "terrestrial only" classes).
  - **Purple** = published vertical benchmark (provincial or federal).
  - **Not shown:** destroyed monuments, and unpublished ones (low horizontal accuracy, preliminary).
  - Clicking a triangle says which kind it is. The line under the map gives the colours.
  - The public list has no "anomalous" flag, so a monument the province lists as published but notes as disturbed still shows green. Open its record from the button to read the condition notes before relying on it.
- **Checked:** 7 new scripted checks on the filter (each of the province's seven classes, a blank class, and the older MASCOT layer); the 143 checks from 1.46.0 unchanged. The class codes were read from the province's own map legend for the layer. Not checked by hand in Chrome.

## Build 1.46.0 — 2026-11-24
The PM and job map items noted Nov 20 to 24, built together. The Strata plan work for townhouses is held for a later build.
- **PM › Job map: house numbers (new).** Each lot shows its civic number (for example 16168), from the BC Address Geocoder, lettered above the PID and plan. Tick box *Addresses*, on by default and remembered; shown once zoomed in to about a block; carried onto *Save map image*.
  - Only the number is shown; the street names are already on the map. A building with many units shows its number once. A lot with several numbers shows the first two and a count.
  - With *Lot labels* off, the numbers are shown by themselves. On a small lot the number is kept and the plan, then the PID, give way.
- **PM › Job map: lot labels (new).** Each lot in view is lettered with its PID and plan number, as on ParcelMap BC. Strata parcels show "Building Strata" and their plan. Narrow lots are lettered sideways. Tick box *Lot labels*, on by default and remembered; shown once zoomed in to about a block. They carry onto *Save map image*.
  - The public ParcelMap BC data has no lot number or district lot, so those are not shown.
- **PM › Job map: provincial control monuments (new).** Green triangles for the province's geodetic control monuments, with the tablet marking beside each when zoomed in. Click one for its GCM number and a button that opens its record (coordinates and elevation are there). Tick box *Monuments*, on by default and remembered.
  - Read from the province's current GeoNetBC layer; the older MASCOT layer is used if that one doesn't answer.
  - Our own control (OCN and other tags) is not in that data; it still comes from a job's .msz.
- **PM › Job map: a job's points straight from its folder (new).** Click one of our job pins and press *Points from this job's folder*. The .msz files in that job's folder on this computer are listed, newest first, with their subfolder and date; one click puts that file's control and pins on the map. Nothing goes through SharePoint.
  - *Add points (.msz)…* now opens in the folder of the last job pin you clicked (otherwise in Job Files - Documents).
  - Automatic backup copies (.mbz, archive folders) are left out; files under Obsolete are listed last.
- **PM › Job map: a job at the quote's own address was hidden (fix).** It sat exactly under the green pin. The green pin now gets a blue ring and reads "this quote · job 26-3687". Clicking it lists the job as before.
- **PM › Job map: new jobs without a refresh (fix).** The pins were read once when the page opened, so a job added to the jobs master afterwards showed in the warning line but not on the map. The map now reads the master again when the file changes (checked when the map is drawn, every half minute, and when you come back to the window).
- **PM › Job map: points and messages reset for each quote (fix).** A note such as "26-3594-PL.msz isn't in UTM" stayed on screen under the next quote, and added points carried over too. Both now clear when you move to another quote. Extra addresses on the same quote keep them.
- **PM › Job map: Remove and Clear all points.** Each added file has a *Remove* button in place of the small ✕, and *Clear all points* appears when more than one file is on the map.
- **PM › Quotes: Copy folder path (new).** Beside *Download quote*. It copies the path of the quote's folder on this computer; paste it into File Explorer's address bar (Ctrl+L, Ctrl+V, Enter). A web page can't open File Explorer itself.
  - The first time on each computer it asks where Quotes - Documents is (paste the path from File Explorer's address bar). It is kept on that computer only and can be changed.
- **PM › Job details: notes for whoever takes the file over (new).** Written with asterisks so they stand out in the text file.
  - Client row: `Client: Randeep Gill **existing client #009**` when the client is in the client list by the same email or the same name. A line under the Client box says so and has **Not the same client**; press it and the note is left off that quote (with Undo). A name that is only nearly the same is never noted.
  - Additional Task Details: `… **existing job 22-2165**` whenever a job in the jobs master is at exactly the same site address, whether or not the quote was made a sub-quote. A neighbouring number is not noted.
  - The notes are in the job details file only: not in the Word quote, its file name or the tracker row. Opening a job details file in the app again takes them off and works them out fresh.
- **PM › Go to: older quotes (fix).** `23-028` answered "no Word quote or job details file". Quotes from before the app went out as PDF, and their job details were filed in the job folder. Go to now looks the quote up in the jobs master and opens `23-2165-job details.txt` from that job's folder, saying where it read it. If there is still nothing, it lists the quote's PDF (opens in a new tab) and any sub-quotes in the folder.
- **PM › Address search could sit on "Looking…" for ever (fix).** Reported from another PM's computer. The search read the quotes master, To Do Quotes, the newest 25 quote folders and the jobs master, and showed nothing until all of them had answered, with no time limit. Where the quote folders are cloud-only in OneDrive, or the browser's permission prompt was waiting, it never came back.
  - **The masters answer first.** Quotes from the quotes master and To Do Quotes show at once, then the jobs. The newest quote folders (those the master doesn't hold yet) are looked at afterwards, and a line is added if one of them is at that address.
  - **Only the small job details file is opened** in those folders, never the Word quote.
  - **Every wait has a limit.** A folder that doesn't open in time is named ("still loading from OneDrive") and the search ends. It keeps reading behind the scenes, so the next search usually has it.
  - **If the browser is waiting for permission, it says so:** look for the prompt beside the address bar, choose Allow, press Go again.
  - The same limits apply to the address check under a quote's site address. *Create next quote folder* still does the full check and waits longer for the newest folders, since that is where a duplicate matters most.
- **PM › Go to and Convert: quote numbers below 100 (fix).** A quote such as 23-060 could not be matched to its own files, because the file name was read as "23-60". Found while fixing the item above; it would have affected every quote 001 to 099 at the start of a year.
- **PM › City GIS button: Cultus Lake and the rest of the Fraser Valley Regional District (fix).** An address at Cultus Lake, Lindell Beach, Deroche, Lake Errock, Harrison Mills, Hemlock Valley, Sunshine Valley, Boston Bar and the other unincorporated areas had no city map, so the button offered nothing. These now open the FVRD web map.
  - The address lookup now keeps the electoral area the province gives for an address, so any address in an FVRD electoral area (A to H) gets the FVRD map even if the place isn't on the list above, or if "Chilliwack" was typed for a Chilliwack River Valley address.
  - Chilliwack, Abbotsford and Mission addresses keep their own city maps. Hope, Agassiz (Kent) and Harrison Hot Springs are municipalities and are not changed.
- **Training: four new videos, one link repaired.** Found in SharePoint › Training Videos and not yet linked: *Map — points over the aerial photo (Points tab)*, *Building layout — first test (Design calc)*, *Strata plan — duplex units (Design calc)*, and *Job map — a job's .msz for control and legal* (PM tab). The Map tool on the Points tab and the PM job map each show a ▶ Training link to their video.
  - *Fixing tree sizes to imperial* pointed at a file that has since been renamed in SharePoint; the link now opens it again.
- **Checked:** 143 new checks in a scripted browser, on made-up folders, client list and jobs master: job map (24), lot labels and monuments (21), job details notes (23), Go to (10), Copy folder path (9), address search (17, including folders that never open, a permission prompt that is never answered and a quotes master that never arrives), house numbers (13), Fraser Valley map and training links (19), whole page (7). The address lookup was asked from Chrome about 15 Fraser Valley addresses to see what it returns (Cultus Lake: "FVRD Electoral Area H"). From Chrome, on the live site's address: the lot, monument and address requests return data (67 addresses around 16120 96 Avenue in under a tenth of a second); the lot and monument requests exactly as the app sends them return data (18167 16 Avenue: PID 012-544-230, plan NWP1455RX, in a quarter of a second; 77 monuments around it).
- **Not checked:** by hand in Chrome, and the address search has not been tried on the computer where it hung, so the cause there (cloud-only folders or a waiting permission prompt) is not confirmed. The new training links were checked against the file names listed in SharePoint, not by playing each video. In particular how the house numbers, lot labels, monument triangles and the ring on the green pin look on the real map, the file picker opening in the job folder, and Copy folder path on a real quote folder. The earlier checks from 1.45 and before were not re-run (their scripts were not available); the parts of the app outside the PM tab were only confirmed to still draw.
- **To know:** the job details notes need Quotes - Documents and Job Files - Documents connected on that computer; without them no note is written. The client list is the one the daily task keeps up to date.

## Build 1.45.2 — 2026-11-20
Three things from the first minutes on 1.45.1.
- **PM › Job map: our job pins were missing (fix).** When a quote was open as the page loaded, the map could be drawn before the app had read which folders are connected. It then showed "Connect Job Files - Documents…" with no blue pins, and never looked again. It now looks again each time the map is shown, so the pins come up by themselves a moment later. If Job Files - Documents really isn't connected on that computer, the line still says so.
- **PM › Services Provided typed by hand (fix).** In 1.45.1 a service was only loaded for quotes coming in from a tracker row or an email block; typing "topo" did nothing visible. Now, when you leave the Services Provided box (or the task details) and the quote's services are still empty, the matching service is loaded, with the same blue line and Remove. Nothing moves while you are typing. It happens once per quote: after a Remove, the service is offered as a button and not loaded again by itself.
- **PM › Job map: street names (new).** Over the aerial photo the map now shows street names and road lines (tick box *Street names*, on by default, remembered). The street map view already has its own.
- **Checked:** pins appear after the folders are read, on a test that fails on 1.45.1; typed "topo" loads Topographic survey on leaving the box, the cursor stays in the box moved to, and it is not loaded twice; street-name tiles are requested and removed with the tick box (7 + 5 new checks). All earlier checks unchanged. Scripted browser, not by hand in Chrome.
- **Not checked:** how the street names look on the real map. The source was tried from Chrome and returns road tiles for Surrey down to one zoom step short of the closest view, so at the closest zoom the names are enlarged and may look soft.

## Build 1.45.1 — 2026-11-20
Two more things asked for before 1.45.0 was uploaded. Includes everything in 1.45.0 below.
- **PM › Services filled from the request (new).** A quote that comes in from a tracker row or an email block now arrives with its service already loaded when Services Provided names one of the plain cases. The approved library wording is used; hours and prices are never set.
  - **Topo / topographic survey:** Topographic survey. If the request is for an **addition or renovation**, House details is switched on. For a **development or subdivision**, Current Legal property line + Area calculation and Visible utilities + Inverts are switched on (and the two plain lines they replace are switched off). For a **new house**, Visible utilities + Inverts.
  - **Property line survey / PL survey:** Property line survey (fencing).
  - **A neighbour issue or dispute, or property corners to be installed:** PL survey & posting plan when it goes with a property line survey or a dispute; Posting plan to set permanent legal markers when it is only corners or posting. "Posting plan for permit" loads that one.
  - **New construction:** New House Construction (the Vancouver version for a Vancouver address, New Construction for multi-family or commercial). "Topo and new construction" loads both.
  - A blue line above the services says what was filled and why, with **Remove** beside each.
  - Things mentioned only in the task details (a building location, for example) are offered as buttons and never added by themselves.
  - Only a quote whose services are still empty is filled. A quote typed by hand gets the same services as buttons to click, not filled for you.
- **PM › Client suggestions for repeat clients (new).** Typing in Client, or in Email, lists matching clients from the client list, newest first, with their email and client number. Picking one fills the client name, and the email if the Email box is empty.
  - Nothing already in a box is replaced: an email that is there stays, and a note says the list has a different one. A quote pasted from the tracker is left exactly as pasted.
  - The note under the box gives the client number and the dashboard's remark for that client.
  - The list is read from `Quotes - Documents › Client List` on this computer. The app keeps no copy and sends none of it anywhere.
- **Checked:** 27 checks on the services, run against the real library: the carport request on Nov 20 loads Topographic survey with House details on and offers the building location as a button; "Topo, Posting, and New House Construction" at a Vancouver address loads all three; subdivision, plain topo, PL survey, dispute, corners, permit; "neighbour" on its own is not treated as a dispute; a quote with services is never changed. 12 checks on client suggestions with a made-up list. All earlier checks unchanged. Scripted browser, not by hand in Chrome.
- **To know:** the phrases it recognises are a first list. If a request you'd expect to be caught isn't, or one is caught wrongly, tell me the wording and it is a one-line change.

## Build 1.45.0 — 2026-11-20
The ten items noted on Nov 20, built together. Most are on the PM tab; the last is in Coordinate design.
- **PM › The address check now reads everything (fix).** A request that was already in To Do Quotes, with its quote folder made and the quote sent, came back as "not quoted before". Two gaps caused it: tracker rows with no quote number were skipped, and a quote folder newer than the quotes master was never looked at. The check now covers:
  - **To Do Quotes rows with or without a quote number.** A row with no number shows as "In To Do Quotes, no quote # yet", with the client, the date requested and who it is assigned to.
  - **The last 25 quote folders.** Any that the master doesn't hold yet are read for their site address (job details file, else the app's Word quote).
  - **The quotes master**, as before.
  - The heading reads **Being quoted now** when the match is a tracker row or a new folder, **Quoted before** when it is from the master.
  - The line says what was checked, for example "quotes master (4,981 quotes, to 26-686) · To Do Quotes (39 rows) · the last 25 quote folders (to 26-691)", and names any new folder it could not compare because it has no address on file yet. "Not quoted before" is no longer claimed.
  - The request you are quoting is not flagged against its own tracker row (same email, or same client or contact name).
- **PM › Warning before a quote folder is created (new).** *Create next quote folder* looks again, fresh, at that moment. If any address on the quote already has a quote or a job it stops and says "There is already a quote with that site address" (or "…a job at that site address"), lists what it found, and asks "Are you sure you want to proceed?".
  - Buttons: **Cancel** (the default), **Belongs to an existing quote…** and **Create anyway**.
  - Nothing is created until you choose. A quote with several addresses is warned for any one of them, and the address is named.
- **PM › Site address suggestions (new).** Typing in Site Address lists matches after a few characters: our own jobs and quotes that start the same way first (marked with their number), then the BC Address Geocoder. Arrow keys and Enter, or click. Picking one puts in the tidy address and its map position, so the checks and the job map run straight away. Works on every property line of a quote.
- **PM › PID from ParcelMap BC (new).** After an address is picked, the PID of the parcel under it is filled in from the public ParcelMap BC layer, with a note giving the plan number and "public record, confirm against title".
  - A PID already in the box is never replaced; a difference is pointed out with a button to use the other.
  - Several parcels under the address: you choose. An address typed by hand gets a **Find PID** button instead of an automatic fill.
- **PM › Legal description from LTSA, by copy and paste (new).** The research button is now **LTSA map — this lot** and opens LTSA's map centred on the lot (sign in to LTSA first). Click the lot there, copy the Parcel Summary, and use **Paste LTSA parcel summary** (or paste straight into the PID or Legal Desc. box): the PID and the full Legal Description are filled from it.
  - If the pasted PID isn't the parcel ParcelMap BC shows under the address, it says "Check the lot".
- **PM › Job map: every address, and a job's points (new).**
  - **Several addresses:** each property of the quote gets its own green point, labelled with its address, and the map opens to fit them. An address that can't be placed is named under the map.
  - **Drop a .msz on the map** (or *Add points (.msz)…*): the control and found pins of a nearby job are drawn with their point numbers — a triangle for survey control, a dot for pins and posts — using the same control-layer list as Points › Map. *Show every point* shows the rest. Click a point for its number, description, file and coordinates. Several files can be on at once, each in its own colour.
  - **UTM only:** a file that isn't in UTM, or mixes UTM with other coordinates, is refused by name and nothing is drawn. A UTM file more than 2 km from the address is held back with the distance until you say *Show it anyway*.
  - **Save map image:** a picture of the map as it stands (photo, lot lines, pins, points, scale bar), with the quote number, address and date on it. *Also save it into the quote folder* writes that one file when clicked.
  - The points are on the map for the session only; nothing is added to the quote.
- **PM › Scope page: mark up the aerial (new).** Each scope page has **Mark up…**: Cloud (the default, in red), Outline, Line, Arrow, Box, Text and Move, in red, blue or black, with Undo (Ctrl+Z), Delete and Clear all. The marked-up picture is what goes into the Word quote as the scope page. The untouched picture is kept with it, so *Edit marks* reopens the same marks later.
  - **More ways to bring the picture in:** pictures and PDFs found in the quote's folder are listed under the panel (click one to add it and mark it up), and **+ From the job map** takes the map as you have it. Pasting a screenshot, a picture file and a PDF page work as before.
  - **Crew copy (PDF):** the page as a one-page PDF titled SCOPE OF WORK with the quote number, address, client and date. It is saved into the quote folder when clicked (downloaded if the folder isn't found), so it is copied to the job's Office folder with the rest when the quote becomes a job.
- **PM › New quote from an email (new).** *New from an email…* gives an instruction to copy into Claude or ChatGPT with the request email under it. The assistant answers with a short labelled block; paste the block (Ctrl+V anywhere on the PM tab) and the quote is started with client, contact, email, phone, site address or addresses, services, task details and date. A quote number, hours or a price in a block are ignored. All the address checks then run as usual.
- **PM › Go to box and links (new).** A box at the top of the PM tab:
  - **A quote number** opens its draft, or reads it from its quote folder if it isn't on this computer.
  - **A job number** shows its address, quote and where its folder is, and whether the folder exists.
  - **An address** is checked against the quotes, To Do Quotes, the newest folders and the jobs master, without starting a quote.
  - **"convert 26-691 to 26-3688"** opens the job conversion with both numbers filled. Nothing is created until *Create job folder* is pressed.
  - The same as links: `#quote=26-690`, `#job=21-1664`, `#convert=26-691&job=26-3688`, `#find=<address>` on the end of the app's address.
- **PM › Jobs: is the client already in the dashboard? (new).** Converting a quote now shows a client step first. The quote's email and name are compared with the client list (`Quotes - Documents › Client List › Elev_Clients_Master.csv`, kept up to date by the daily task).
  - Matches by email (capitals ignored, every address in the box), then by the company's own email domain, then by name, including near-misses in spelling. Each match shows the client number and why it matched, with a button to copy the number.
  - An email shared by several clients lists all of them. Nobody found: "New client", with the name and email ready to copy into the dashboard.
  - The list is read on this computer when needed. The app keeps no copy of it and sends none of it anywhere.
- **PM › Jobs: job number from the dashboard's CSV (new).** *Read the job # from the dashboard's CSV…* takes the Job list's Download CSV file and fills Job # from the row whose Contract is this quote (003687 with an order date in 2026 becomes 26-3687; contract 26-135-B matches quote 26-135B). It says so if the address differs from the quote's, or if no job has that contract yet.
- **Coordinate design › Lines as polylines (new).** *Lines as polylines (.dxf)* writes each picked line (gutter line, centre line and so on) with its design elevations:
  - **A 3D polyline** through the line's design points, with the **BC, midpoint and EC** of every curve. These are the same positions and elevations as the INTERP points in the points file.
  - **The same line in 2D with true arcs**, for offsets.
  - **Optional:** a 3D copy with the curves chorded to within 1 cm of the arc, on its own layer.
  - Calculated elevations are straight-line between the design values on either side, by distance along the line, and are labelled CALC in the drawing. Nothing is extrapolated: a stretch before the first or after the last design value is left out of the 3D line and reported ("NO ELEVATION for 5.0 m at the start").
  - The panel lists each line before saving, and the Summary lists every polyline point with its source.
- **Checked:** by script in a test browser, 145 new checks, with the earlier ones unchanged.
  - Address check and warning (21): a tracker row with no number and a folder newer than the master are both found; own request not flagged; warning on a quote, on a job, on the second of two addresses; Cancel creates nothing.
  - Suggestions, PID, LTSA paste, several addresses (23). The three outside services were also tried from Chrome on a real address: suggestions returned, and the PID matched the one LTSA shows for that lot.
  - Client check and job CSV (17), against the real client list and the real Job list export.
  - Points on the job map (19): control and pins found, a point lands 13.0 m from the address where the test file puts it, local and mixed files refused, far file held back.
  - Mark-up and crew PDF (27): every tool, Undo, Move, Delete; the cloud bulges outward whichever way round it is clicked; the PDF opens as one letter page.
  - Email block, Go to box and links (23).
  - Polylines (15): on a line with a 90° curve of radius 10, BC, MID and EC are on the true arc with the right elevations; the DXF was opened in a second program, which read the arc back as centre 20,10 radius 10.
- **Not checked:** none of this has been run by hand in Chrome yet. In particular: pasting a real Parcel Summary copied from LTSA (the reader was written from a screenshot of the panel); *Save map image* and *+ From the job map* end to end (the photo and lot-line sources do allow copying, tried from Chrome); the polyline DXF opened in MicroSurvey; a real .msz from a UTM job.
- **To know:**
  - Only the address text typed, and one map position, are sent out (to the BC Address Geocoder and ParcelMap BC). Nothing about the client or the quote is.
  - The PID comes from the public parcel map, not from title. The legal description only ever comes from what you paste from LTSA.
  - The client heads-up is as current as the client list file. It says "as of" with the list's date.
  - A new quote folder with nothing in it yet can't be compared by address; it is named on the "Not compared" line until its job details file is saved.

## Build 1.44.1 — 2026-11-19
What Strata plan gained in 1.43, brought to Building layout where it applies. Includes 1.44.0 below.
- **Building layout › Undo takes back any step (new).** Undo on the toolbar used to cover outline edits, post lines and excavation edits only, and only in the step they belonged to. It now takes back the last change on the page whatever step it was in: scale, outline, confirming the outline, each post, confirming posts, the lot pick, setback rows and placement, the excavation and edits to it. It works from the Plan and the Site view, up to 60 steps back.
  - A drag, or a burst of typing in one box, counts as one step.
  - The house position is worked out again from the setbacks after an Undo, so it always matches what is on screen.
  - Turning the plan or changing page starts a fresh list.
- **Building layout › Always clear which step is on (new).** The same strip as Strata plan, above the plan: 1 Scale · 2 Outline · 3 Posts · 4 Lot · 5 Setbacks · 6 Excavation · 7 Output. The step that is on is solid blue, finished steps are ticked, steps not yet reachable are grey. Click one to go there.
  - Only the card of the step that is on is open; the rest are folded to their heading. The floor-elevations card opens and closes on its own as before.
  - Clicking a step's heading always makes it the step that is on.
- **Building layout › Dimensions keep clear of more linework (change).** The building dimensions already kept off the house lines, each other and the elevation block. They now also keep off posts, post lines, the excavation line and the lot lines, and a dimension slides along its side when the middle is taken. Any that still can't be placed clear are listed in the save message so they can be moved in CAD.
- **Not carried over, because they don't apply:** wall-centre snapping and cutting areas out of a lot (Building layout works to the outside face of the foundation), separate blocks, floors and automatic floor saving, the Adding switch. Reopening a job from the plan and the app's DXF has covered Building layout since 1.43.
- **Checked:** a job taken through scale, outline, two posts, lot, setbacks and excavation, then undone one step at a time back to an empty page, with nothing put back on the list by undoing; strip and card headings; a post standing where a dimension would go, and the dimension placed clear of it (16 checks). All earlier Building layout and Strata checks unchanged. Scripted browser, not by hand in Chrome.
- **To know:** Undo does not bring back a lot drawing that was loaded and then replaced, or a plan that was turned; it covers what was worked out on the page, not which files are open.

## Build 1.44.0 — 2026-11-19
- **PM › Job map with lot lines (new).** The map preview under a quote's site address now opens on a map the app draws itself, instead of the Google job map.
  - **Background:** aerial photo or street map, with **ParcelMap BC lot lines** over it (tick box to turn them off).
  - **This quote's address:** a green pin.
  - **Our jobs:** a blue pin for every job in the jobs master that has a position, labelled with its job number when zoomed in.
  - **Click a job pin:** job number, quote number, address, how far it is from this quote's address, and *Make this a sub-quote of …* (the same button as under *Existing job*).
  - Drag to move, wheel or + / − to zoom, *Re-centre* to come back.
  - **Google job map** is one click away on the same bar, and the choice is remembered. *Open in My Maps* is unchanged.
  - Job pins need Job Files - Documents connected under *Folders on this computer*; without it the map still shows, with a line saying so.
- **Jobs master now has coordinates (data, not the app).** All 2,678 rows of `Elev_Jobs_Master` carry a latitude and longitude as of today, so the *Existing job* check finds a job within 75 m on any street, not only on the same street. The weekly job map task fills them in for new jobs.
- **Checked:** with the real jobs master, a quote at 14040 103A Avenue shows the pin for job 21-1664 next door; clicking it gives "Job 21-1664 · quote 21-736 … 14 m from this quote's address" and the sub-quote button; lot-line and photo tiles are requested for the area; switching to the Google map and back; with Job Files not connected (11 checks). All earlier checks unchanged. Scripted browser, not by hand in Chrome.
- **Not checked:** that the photo and lot lines actually load in this view; they could not be loaded where the build is tested. They use the same sources as Points › Map, which is reported working.
- **To know:** 137 jobs are positioned along their block rather than on the lot (marked in the master's Notes column), so their pins can sit a few lots off. Lot lines are ParcelMap BC's and the photo is good to a metre or two: a guide, not a survey. Only site addresses are sent to the BC address finder; job pins are drawn from the file on this computer.

## Build 1.43.5 — 2026-11-18
From running the Delta job through three floors on 1.43.1. Includes everything in 1.43.4 and 1.43.3 below, which were not uploaded.
- **Strata › Floors no longer overwrite each other (fix).** Two pages could both be given the name "Floor 2", and saving the second replaced the first: the upper floor took the main floor's place and the totals lost a floor. A saved floor now belongs to the outline it was made from, not to its name.
  - *Update* on a page changes that page's floor only. Typing a new name renames it in place.
  - If another floor already has the name, this one takes the next free "Floor n" and the message says so.
  - New floors are named with the first free number, and the list is kept in page order.
  - A different outline picked elsewhere on the same sheet counts as another floor.
- **Strata › Floors save themselves (new).** Once a floor's lots are confirmed it is saved when you turn to another page and before any export, so the totals and the DXF always have the latest. *Save this floor* / *Update* is still there for seeing the totals change straight away.
- **Strata › Always clear which step is on (new).**
  - **Step strip above the plan:** 1 Scale · 2 Outline · 3 Walls · 4 Lots · 5 Non-habitable · 6 LCP · 7 Floors · 8 Output. The step that is on is solid blue, finished steps are ticked, steps not yet reachable are grey. Click one to go there.
  - **Adding switch in steps 5 and 6:** "Adding: Non-habitable | LCP" at the start of the tool bar, coloured like the areas. It shows what the next area drawn will be, and clicking the other one changes step and tool together.
  - **One card open at a time:** only the card of the step that is on is open; every other step is folded to its heading, with its tick and summary. Saving a floor by hand moves to step 7. Clicking a step's heading always makes it the step that is on; before, clicking the heading of a card that was already open closed it and left the other step on, so an area meant as non-habitable could go in as LCP or the other way round.
- **Strata › Only real garages are offered (fix).** On the upper floor step 5 offered "4 garages found", which were bedrooms the outline pick had closed across. A closed-off room is now offered as a garage only when the plan labels it GARAGE, CARPORT or PARKING.
- **Checked:** three pages begun with the same floor name end as three floors in page order, by page turns alone; an area added and the page left is in the saved floor; a change followed straight by an export is in the export; a job in the state on the 16:02 screens gets its main floor back beside the upper floor (14 checks). Strip, switch and card headings (8 checks). All earlier checks unchanged. Scripted browser, not by hand in Chrome.
- **To know:** to carry the Delta job over, press Strata DXF on 1.43.1 first, upload this build, then drop the PDF and that DXF on Design calc and turn through pages 3 and 4. The main floor is saved by itself as "Floor 3"; type the names you want in the "This floor" box.

## Build 1.43.4 — 2026-11-18
From tracing the deck LCPs on the Delta plan in 1.43.1: the corners kept jumping to the blue strata line. Includes everything in 1.43.3 below, which was not uploaded.
- **Strata › Tracing an LCP no longer jumps to the blue line (fix).** In 1.43.1 every point near a wall was pulled to the strata line or a wall centre from up to 60 px away, which is right for a garage wall and wrong for a deck. For an LCP the snap is now:
  - **A corner or line end drawn on the plan** (deck edge, post, wall face), as it was before 1.43.
  - **The green outline** (the outside face of the building): a corner of it, or anywhere along a side when nothing drawn is closer. The marker shows which it has caught.
  - Never the blue line or a wall centre. Dragging an LCP corner in Move follows the same rule.
- **Strata › LCP: pick the green line and it runs on to the blue (change).** A side picked on the green outline is moved square on to the strata line when the area is finished, so the LCP meets the lot with no gap. This was already the rule; in 1.43.1 the sides were also being shifted onto the centre of double lines such as guardrails, which is why the result didn't sit on the deck edge. That shift is now for non-habitable areas only.
- **Strata › LCP squaring (change).** A point clicked in the open is squared to the point before it when the line is within 6° of square to the building. A point picked on a drawn corner never moves; a point picked along the green line may slide along it to square up.
- **Strata › Non-habitable: wall-centre snap is less grabby (change).** A wall centre or strata line is taken when the click is on or beside the wall (25 px, was 60). A drawn corner right under the cursor (6 px) wins when it is the nearer.
- **Checked:** on the Delta main floor, seven points near walls give a drawn corner, the green line or nothing when tracing an LCP, and wall centres or strata lines when tracing non-habitable; an LCP started 1.5 units off the green line with two rough clicks in the open comes out square with its wall side on the blue line (4 + 5 checks). The garage cut and the earlier LCP checks are unchanged. Scripted browser, not by hand in Chrome.
- **To know:** LCPs traced in 1.43.1 keep the edges they were given; re-trace them, or drag the side once in Move.

## Build 1.43.3 — 2026-11-18
Two fixes from the first run of 1.43.1 (1.43.2 was filed but not uploaded; its change is the first one here).
- **Strata › Separate blocks joined by a thin strip (fix).** On the Delta upper floor the picked outline runs across between the two units along the bottom, 0.15 m (one wall thickness) above the outside line, so the blocks were joined by a sliver and the app asked for a party wall. A strip under 0.6 m wide is now closed up and the floor is read as separate blocks, one lot each, with no party wall to pick.
  - Before, the blocks had to meet at a line of no width (within 2 cm).
  - A link 0.6 m or wider is left as one outline, since it could be a passage.
  - The confirm message reads "2 separate blocks on this floor, so no party wall is needed".
- **What's new card (fix).** The card on the first screen showed the section headings and sub-points of the release notes run together with their markdown marks. Sub-points are now listed under their item, headings and marks are left out, and the test notes are not shown.
- **New in 1.43 (details under Build 1.43.1 in CHANGELOG.md):**
  - Points › Map: a UTM 10 points file over an aerial photo, control highlighted.
  - PM: a pasted tracker row is checked against the jobs master, and one click makes it a sub-quote of the existing job's quote without clearing anything.
  - Design calc: drop the plan, then the app's DXF, to reopen a strata or building layout job.
  - Strata: cut a garage out of a lot by drawing only the dividing wall; corners go to wall centres; one label per area; TA and THA; labels and dimensions kept clear; CSV for lots only.
- **Checked:** the Delta upper floor with the strip at 0.15, 0.30 and 0.55 m gives two lots of 65.8 m² each; at 0.9 m it stays one outline (10 checks). The card was rendered from this file. All earlier checks unchanged. Scripted browser, not by hand in Chrome.

## Build 1.43.1 — 2026-11-18
Ten things asked for over the last two days, built together. Builds 1.42.4 and 1.43.0 never needed uploading; everything in them is in here (1.43.1 only adds the last CSV change below).

### Points
- **Points › Map (new).** With a points file open, the Map button (in *Clean up a topo*) puts every point over an aerial photo.
  - **Survey control is a red triangle with its number and code; pins and posts are yellow; every other shot is a small blue dot.** Control is every code the 2026 AutoMap puts on the CONTROL layer. Pins and posts are the IP / LP / RP / pipe / rebar codes within that list.
  - Click a point for its number, description, N / E / Z and a link to the same spot in Google Maps. Drag to move, wheel or + / − to zoom, *Fit all* to come back.
  - Background: aerial photo, street map, or none. *Lot lines (ParcelMap BC)* can be switched on over it. *Number every point* labels the ordinary shots too once zoomed in.
  - Coordinates are read as NAD83(CSRS) UTM zone 10. A local or assumed job gets a line saying why there is no map.
  - Nothing from the file leaves the computer; only the picture tiles for the area in view are requested.

### PM
- **PM › Is there already a job here? (new).** Under the site address, next to *Quoted before*, the draft is checked against `Elev_Jobs_Master.csv` in Job Files - Documents.
  - **Same address:** "Existing job: 21-1664 · quote 21-736 (same address …)". St / Street, unit numbers and "BC, Canada" don't matter.
  - **Close by:** a job on the same street within 40 house numbers is listed as "Job close by", with the distance in metres when the BC address finder knows both addresses (anything over 150 m is dropped).
  - **On paste:** when tracker rows are pasted, the message says straight away which of the new drafts sit on an existing job.
  - Needs Job Files - Documents connected under *Folders on this computer*. The file is only read.
- **PM › Make this a sub-quote, keeping the row (new).** Beside each job found is *Make this a sub-quote of 21-736*. The draft becomes the next free letter (the quote folder is checked, so 21-736C if B is there) and **nothing is cleared**: client, contact, Services Provided, task details, PM comments, date requested, hours and prices all stay. Blank job details are filled from the original quote when its file is found. It asks before changing anything, and it creates no folder; the quote saves into the original quote's folder as sub-quotes already do.
  - *Belongs to an existing quote…* on the top bar does the same when you know the quote number and the job isn't in the master.
  - *Duplicate as sub-quote* is unchanged: a blank sub-quote of the draft that is open.
- **PM › Duplicate as sub-quote from a draft with only the Quote # typed (fix).** It stopped part-way and fell back to copying the empty draft. It now reads the original quote from its folder as intended.

### Design calc
- **Reopen a job later (new, Strata plan and Building layout).** The DXF the app writes now carries the working data, as comment lines CAD ignores.
  - **To carry on with a job:** drop the architect's plan on Design calc, then drop the app's DXF (either order). Scale, outline, wall readings, strata lines, lot names, non-habitable and LCP areas and every saved floor come back; other pages come back as you turn to them. Edit, *Update* the floor, save again.
  - **Building layout:** the outline, posts, setback rows, floor elevations and excavation come back, a turned plan is turned the same way, and the message then asks for our lot drawing. Drop it and the lot and the house position return. Both *DXF (calc only)* and *Lot lines + calc* carry the data.
  - A tick box beside the DXF button turns this off if a plain DXF is wanted.
  - If the DXF has been re-saved from CAD the data may be gone; the app says so and changes nothing. Keep the DXF the app wrote.

### Strata plan
- **Step 5 › Cut from a lot (new, and now the tool that is on when step 5 opens).** For a garage or any room inside a lot, draw only the wall that divides it from the rest: click along it, double-click to finish. The other sides follow the strata lines already there. The message gives both areas, and *Other side* swaps them if the wrong part was taken.
- **Corners and sides go to the centre of the wall (new).** In Cut from a lot, Trace area and when dragging, a point near a wall goes to the wall's centre line, interior walls included; a strata line already there wins over a wall, and a corner lands on a corner. A side drawn along a wall is moved onto that wall's centre as a whole. Lines within 6° of square are made square. The marker shows what it has caught.
- **Garages are offered (new).** A garage door closed across when the outline was picked is remembered, and step 5 offers it: *Mark as non-habitable* takes it to the centre of the walls round it.
- **Names from the plan (new).** A new area is named from the room label inside it (GARAGE, DECK, …) when there is one.
- **Floors where the units are separate blocks (new).** When the outline is two or more blocks that don't touch (an upper floor with roof between the units), each block is a lot and step 4 has no party wall to pick.
- **Output › One label per area (change).** An LCP shows only its name (an unnamed one reads "LCP SL 1"), with no area figure. A non-habitable area shows its name and area. Nothing is labelled twice.
- **Output › TA and THA (change).** On the floor chosen for totals each lot shows **TA** = every floor, habitable plus non-habitable, and **THA** = total habitable when the lot has any non-habitable. LCP is in neither.
- **Output › Labels and dimensions kept clear (new).** Each label and dimension is placed where it doesn't touch another or cross linework; a name that won't fit inside a small area goes beside it with a leader; a dimension is written once per line. Anything that still couldn't be placed is listed in the message so it can be moved in CAD. Sides under 0.10 m are not dimensioned, and the count is given.
- **Areas (.csv) (change).** Strata lots only: habitable, non-habitable and total for each floor, then *ALL FLOORS* for each lot. LCP areas are left out. Non-habitable areas are listed by name underneath. **When no floor has a non-habitable area, the habitable and non-habitable columns are dropped** and the file is just floor, lot and total.
- **Step 3 "Wall thickness (centre line)"** measures itself when the outline is confirmed and is skipped when every wall agrees; the *Usual outside wall* box shows 0'-8" properly (both from 1.42.4).

### Checked
- **Delta plan, main floor:** three rough clicks cut the SL 1 garage at 40.6 m² on the interior wall centre (834.0, faces at 829.5 and 838.5), party wall line and outside strata lines; a rough trace of the same garage comes to 40.4 m²; the offered garage on SL 2 is 41.2 m² (17 checks). **Upper floor:** two blocks of 65.8 m² each, no party wall (6 checks).
- **Output:** the DXF was read back: no label overlaps another, LCPs carry one label and no area, TA and THA add up (7 checks). **CSV:** an LCP on the floor does not appear; with no non-habitable area the file has the total column only.
- **Reopen:** a two-floor strata job saved, the app restarted, plan then DXF dropped, and both pages compute the same lots, garages and party wall to the millimetre; edited and saved again; DXF-first order; a cut-off DXF is refused (16 checks). Building layout with a turned plan and a lot drawing comes back on the same job coordinates with its excavation (11 checks). The DXFs open in ezdxf and in the app's own reader with the comment lines in place.
- **PM:** against the real jobs master (2,676 jobs), "14036 103A Ave, Surrey" finds 21-1664 / 21-736; 14040 is flagged as close by; 14036 104 Avenue is not matched; the pasted row keeps every field and becomes 21-736C when B is in the folder; Cancel changes nothing (13 checks).
- **Map:** UTM to latitude / longitude agrees with the standard library (EPSG:26910) to 0.1 mm; control, pins and shots are classed correctly; the right photo tiles are asked for (9 checks).
- All earlier checks unchanged, including 25-3402 (TA 315.5 against 315.7).

### Not checked — please look at these first
- **The aerial photo and the ParcelMap BC lot lines could not be loaded where the build was tested** (no internet access there). The points, zoom and scale bar are tested; whether the photo and lot lines appear is not. If the photo doesn't load, the map says so and the points still plot.
- **Distances in the job check** were tested with a stand-in for the BC address finder, for the same reason.
- **MicroSurvey has not opened a DXF with the working-data lines.** Group 999 comments are standard DXF, but if MicroSurvey objects, untick the box and tell me.
- Everything was run in a scripted browser, not by hand in Chrome.

### To know
- The jobs master has no coordinates yet, so a job on a *different* street (a corner lot addressed on the cross street) is not found. Rows that carry a latitude and longitude are compared by distance (75 m) on any street, so this improves if coordinates are added to the master.
- The aerial photo is Esri World Imagery. It needs no key and is shown with Esri's credit; Esri's terms expect an ArcGIS account for regular business use. The background can be switched to the street map or off.
- A photo is only good to a metre or two, and NAD83(CSRS) is about 1.5 m from the photo's datum, so the map shows where control is; it doesn't check it.
- Wall-centre snapping follows the layers the outline was picked on. On a scanned plan there are no lines to read, so points stay where they are clicked.
- Floors saved before this build have no working data inside older DXFs; save the DXF again from this build to be able to reopen it.

## Build 1.42.4 — 2026-11-18
- **Strata › Step 3 is now "Wall thickness (centre line)" and mostly looks after itself (change).** The outline in step 2 is the outside face of the building; this step finds the inside face of each outside wall so the strata line can go halfway between. It used to be a button to press and a second thing to confirm.
  - **Confirming the outline now measures the walls straight away.**
  - **When every side reads, they all agree, and nothing was left out, step 3 is skipped:** you land on step 4 with Pick party wall on, and the message says, for example, "All 12 outside walls read 0'-8" (0.203 m) and the strata line is at their centre".
  - **It only stops at step 3 when something needs a look:** a side that couldn't be read, sides that disagree, a furred wall or finish that was left out, or structure set back behind cladding. The message names which.
  - One Undo from either case goes back to the unconfirmed outline.
  - Step 3 can still be opened to change the usual wall, switch to the outer face, measure again, or set one side by hand.
- **Strata › "Usual outside wall" box showed only "0" (fix).** The feet mark in 0'-8" ended the box's text early. The figure being used was right; the box now shows it. The same fix is applied to the other text boxes in the strata steps (floor and area names).
- **Checked:** a plain duplex goes from confirming the outline straight to step 4, and one Undo returns to the outline. The Delta basement measures by itself (13 of 14 sides) and stops at step 3 because a furred wall was left out on 12 sides. The box reads 0'-8". All earlier checks unchanged, including 25-3402 (TA 315.5 against 315.7). Scripted browser, not by hand in Chrome. Not yet opened in MicroSurvey.
- **To know:** a basement with furring drawn inside the concrete, like the Delta one, will stop at step 3 every time, since leaving the furring out is a judgement worth a glance.

## Build 1.42.3 — 2026-11-17
The rule behind this build: no gaps and no overlaps between the lots and the areas round them.
- **Strata › An LCP drawn to the wall face runs on to the strata line (new).** Trace or pick an LCP to the outside face of the building wall and the side on the wall is moved square on to the strata line at the centre of that wall, so the LCP meets the lot with nothing between them. The message says when that happened. Non-habitable areas already did this; LCP now does too.
  - A corner where two such sides meet lands on the corner of the strata lines.
  - A side that only lines up with a wall past its end is left where it was drawn, so the area stays square.
  - An area away from any wall is left exactly as traced.
- **Strata › The same applies after an edit (new).** Drag a side or corner of an area back near a wall and it goes on to the strata line again.
- **Strata › Overlaps are flagged (new).** In steps 5 and 6 a row shows "overlaps …" when an LCP laps more than 2 cm over a lot or another area, or two non-habitable areas lap over each other. Gaps between two areas that don't touch a wall are not detected; trace both to the same drawn line.
- **Checked:** on the Delta basement, an LCP traced on the wall faces at an inside corner comes out square on the two strata lines (2.02 m²); a free-standing one is untouched; a side nudged 5 cm off the wall goes back; an LCP drawn across the wall into the lot is flagged (7 + 8 checks). The synthetic deck now reads 10.30 m² (4.00 m of wall × 0.075 m more than before), which is the intended change. All earlier checks unchanged, including 25-3402 (TA 315.5 against 315.7). Scripted browser, not by hand in Chrome. Not yet opened in MicroSurvey.
- **To know:** areas already saved on a floor before this build keep their old edges; re-trace them or drag the side once to pick up the new rule.

## Build 1.42.2 — 2026-11-17
From working through the Delta plan's LCPs: editing an area, what the buttons do, and Undo.
- **Strata › The toolbar follows the step you're on (change).** There were 14 buttons, two of them just called "trace". Now there are six or so, and they work on whatever step is open:
  - **Move · Measure · Pick · Trace · Drop · ↶ Undo**, with each button named for the step. Step 2: *Pick outline / Trace outline / Drop corner / side* (plus Straight across and Redraw a stretch, which only apply to the outline). Step 3: *Pick a side wall*. Step 4: *Pick party wall / Draw wall line / Remove a wall*. Steps 5 and 6: *Auto-pick area / Trace area / Drop corner*.
  - The line under the toolbar starts with the step, e.g. **Step 6 · LCP.**
- **Strata › Opening a step switches to its tool (new).** Click a step's heading and the tool it needs is already on: Pick party wall for step 4, Trace area for steps 5 and 6, Pick outline for step 2 when there is no outline yet. Confirming a step does the same for the next one.
- **Strata › Edit an LCP or non-habitable area (new).** In *Move*, every area shows small squares at its corners. Drag a corner (it snaps to the drawing unless Snap is off) or drag a side. *Drop corner* then a click on a corner takes that corner out. The message gives the area before and after.
  - Once the outline is confirmed, an area or party wall wins over the outline where they sit on top of each other, so dragging an LCP corner at the building wall moves the LCP, not the building.
- **Strata › One Undo for every step (change).** *↶ Undo* on the toolbar now takes back the last thing done on the floor whatever step it was in: picking or tracing the outline, an outline edit, a garage door closing, confirming a step, measuring, a party wall, an area, an area edit, Clear outline. Up to 60 steps back. The Undo button in step 2 does the same thing. Clear outline no longer asks first, since Undo brings it back.
- **Strata › Trace is the default for areas; the click-inside pick is now "Auto-pick area" (change).** The pick takes the smallest closed box of lines round the click, so stairs, boards or posts drawn inside a deck break it up. It's kept for clean boxes, second in line, and the step text says when it won't work.
- **Strata › Adding or removing an area no longer un-confirms the lots (fix).** Each LCP used to send step 4 back to "confirm" and lock steps 5 and 6 until it was confirmed again.
- **Building layout › Same toolbar idea (change).** The plan toolbar shows the outline tools on step 2 and the post tools on step 3, instead of all eleven at once. Opening a step switches to its tool (and to the Site view for the lot, setbacks and excavation once our lot drawing is loaded). The line under the toolbar starts with the step.
- **Building layout › ↶ Undo on the toolbar (new).** It takes back the last change in the step you're on: outline edits, post lines, excavation edits. It does not yet cover picked posts, the lot, setbacks or confirmations; those still have their own buttons.
- **Checked:** Delta basement: area drag by corner and side, at an outline corner and along the wall (8 checks); toolbar per step, step opening, Drop on an area and on a wall, and Undo back through eight actions to the unconfirmed outline (14 checks); Building layout toolbar and Undo (6 checks). All earlier checks unchanged (Design calc tab 25, Delta main floor, 25-3402 TA 315.5 against 315.7, Building layout 31). Scripted browser, not by hand in Chrome. Not yet opened in MicroSurvey.

## Build 1.42.1 — 2026-11-17
- **Design calc › Dragging a drawing onto the tab now loads it (fix).** In 1.42.0 a PDF dragged onto the Design calc tab gave "This PDF doesn't contain Elevate Office data, so it can't be imported." The app has one catch-all for dropped files that decides by tab where a file goes; it knew about Points and PM but not the new tab, so it treated the drawing as a checklist to import. Choosing the file with the button worked; dragging didn't.
  - **Now:** a file dropped anywhere on the Design calc tab (on the drop zone or not) opens in the tool that is showing, and is loaded once.
  - A drawing dropped on the Points tab is also loaded once now (it used to be read twice).
  - The Checklists tab keeps its own message for a PDF that isn't an app-made checklist.
- **Checked:** real drop events on the drop zone, elsewhere on the tab, on the Points drop zone and on Checklists (5 checks); the 20 tab checks from 1.42.0; Delta main floor, 25-3402 and Building layout tests unchanged. Scripted browser, not by hand in Chrome.

## Build 1.42.0 — 2026-11-17
- **Design calc (new tab).** Everything that starts from someone else's drawing now has its own tab, next to Points. It holds three tools side by side:
  - **Coordinate design** (the engineer's design drawing),
  - **Building layout** (was Building calc),
  - **Strata plan** (was a switch inside Building calc; now a tool of its own).
- **Pick the tool, then drop the drawing.** The tab has its own drop zone, and a drawing opens in the tool that is showing. The drop zone's wording changes with the tool.
- **Points tab › points-file tools only (change).** The third group is now *Stakeout & monitoring*: Design vs Field and Monitoring. The first two groups are unchanged.
  - A drawing (.dxf / .dwg / .pdf) dropped in Points still works: it opens the Design calc tab and loads there.
  - "Send to Design vs Field" in Coordinate design takes you to the Points tab, where Design vs Field lives.
- **One points shelf for both tabs.** A points file dropped in either tab goes on the same shelf. Coordinate design and Building layout show which job points they are using; Strata plan doesn't use a points file.
- **Kept as it was:** every step, setting, remembered page and output inside the three tools. Building layout and Strata plan still read the same loaded plan, so switching between those two keeps the drawing open. The tab remembers which tool you were in; if you were last in Coordinate design, Building calc or Strata, it opens on that one.
- **Not changed:** the Auto tab.
- **Checked:** 20 checks on the new tab (tools, drop routing for each tool, points file to the shelf, the Points groups, a drawing dropped in Points, remembered tool). The Delta main floor and basement checks, 25-3402 (TA 315.5 against 315.7), the two-floor TA check and the Building layout tests (31) all give the same results as 1.41.26. Tested in a scripted browser, not by hand in Chrome; "Send to Design vs Field" was not exercised. Not yet opened in MicroSurvey.

## Build 1.41.26 — 2026-11-17
From the main floor sheet (page 3) of the Delta plan, where Pick outline gave a 24-corner, 89.7 m² outline that wandered through the inside of both units.
- **Pick outline › Black lines are one layer whether or not the PDF says "black" (fix).** This PDF draws Unit B's walls with the colour set to black and Unit A's with no colour set, which also means black. The app treated those as two layers, followed only one, and so ran out of wall halfway round, whichever wall was clicked. They are now the same layer. This applies to Building layout picks as well.
  - Page 3 now picks both units from one click on any outside wall. The basement sheet (page 2) also comes out the same on both sides now.
- **Strata › Garage door openings are closed (new).** A garage door is wider than the 1 m gap the pick joins by itself, so the outline went in through the door and round the inside of the garage. In Strata, a room of 10 m² or more that the outline has entered through a square opening 1.8 to 3.4 m wide is now closed straight across, and the message says how many and how much area that brought in. On page 3: both garages, 74.9 m², giving 20 corners and 242.5 m².
  - Undo in step 2 takes a closing back, one at a time.
  - These automatic closings don't count as your edits, so picking again doesn't ask "clear your edits?".
- **Step 2 › Clear outline (new).** A *✕ Clear outline* button removes the outline (and, in Strata, that floor's walls and areas) and puts you back in Pick outline with nothing on screen. It asks first only if you had made edits or added walls or areas.
- **Checked on page 3:** pick from three different walls, pick again, clear and pick; *Measure* reads 6" walls on 14 of 20 sides; one click on the party wall gives a 0.330 m wall with the line at its middle and two lots of 118.1 m² each. 25-3402 re-run with the same figures (TA 315.5 against 315.7); the basement checks from 1.41.25 and the Building layout tests (31) unchanged. Not yet opened in MicroSurvey.
- **To know, page 3:** the outline still includes the two small squares at the veranda (posts touching the wall line) and leaves out the recess between the units at the back; drop or keep those as the job needs. Six sides have no second wall line to read and show as assumed.

## Build 1.41.25 — 2026-11-16
From the first strata DXF saved off the Delta plan (9362 114 Street, basement).
- **Strata › Strata line at the centre of the structural wall, not the wall plus its furring (fix).** On this plan the outside wall is 8" concrete with a furred wall drawn 4" inside it. The tool read the two together as a 12" wall and put the line 0.152 m in from the outside face, which is three quarters of the way through the concrete, towards the inside.
  - **Now:** where the first line in from the outline is already a whole wall away (12 to 27 cm), that is taken as the structural wall and anything drawn further in is left out. On this plan every side now reads 8" (0.203 m) with the line 0.101 m in, and 13 of 14 sides are read from the drawing (was 7).
  - The message after *Measure* says when a furred wall or finish was left out, so it can be checked.
  - Wood-frame walls with cladding lines (25-3402 Levels 1 and 2) are read as before; their figures are unchanged.
- **Strata › TA= only when there is more than one floor (change).** TA is each lot's total over all its floors, lettered once, on the floor chosen in step 7. With one floor saved the DXF no longer letters a TA that just repeats the floor's own area. Step 7 says so until a second floor is saved.
- **Also in this build:** everything listed under 1.41.24 below (that build went out in chat only, a few minutes earlier).
- **Checked:** Delta plan, strata line against the drawn wall lines on all 14 sides; one floor saved gives no TA, two floors give one TA per lot. 25-3402 re-run with the same figures on all three floors (TA 315.5 against 315.7). Building layout tests unchanged (31). Not yet opened in MicroSurvey.
- **To know:** one side on the Delta plan (the short one beside the sunken well) still takes the usual wall and shows as assumed. The small LCP pieces round the sunken well in that DXF letter on top of each other at 1:150; that isn't changed here.

## Build 1.41.24 — 2026-11-16
Strata party walls, worked through on a second plan (9362 114 Street, Delta duplex, basement sheet), where the walls are drawn as lines with a dot pattern instead of solid shading.
- **Strata › One click now works on walls drawn as lines (fix).** On this plan the one click found nothing to follow and asked for a second point, and the two clicks then centred on only one half of the double wall, so the line sat off to one side.
  - **Now:** the click looks at the lines either side of it and takes the set that is the same on both sides of its middle. On this plan that is the whole double wall, 0.432 m across (two 8" walls and the gap), with the line at its middle.
  - It doesn't matter whether the click lands in the gap, on a face line or on the outer face: all five places tried gave the same line.
  - The message says the width was read from lines and to check it is the whole wall.
- **Strata › Step 4 is now "Party walls & strata lots" (change).** Outside walls are their own step 3 (*Measure*, then confirm). Step 4 opens with **Select party wall** already switched on, and the toolbar button has the same name.
- **Strata › Draw wall line (new, replaces Wall by hand).** Draw the line that separates two lots yourself: click at one edge of the outline, any corners in between, and the other edge.
  - The line is used exactly as drawn and is trimmed or extended to the outline. Clicking past the edge is fine.
  - It finishes by itself once it runs from edge to edge. A line that doesn't cross a lot is refused and nothing is added.
  - It goes on the `SL` layer as a solid line and is listed as *drawn by hand* in step 4.
- **Strata › Drag a wall line to move it (new).** In *Move*, drag any party wall line sideways. It's listed as *moved by hand*. A move that would stop it cutting a lot is refused.
- **Strata › Undo (new).** *↶ Undo* on the toolbar and in steps 4 to 6 takes back the last thing done on the floor, one at a time, up to 60: a wall selected, drawn, moved or removed, an LCP or non-habitable area, a side-wall setting, a wall measure. While a line or trace is half drawn it takes back the last point. *Remove all walls* and *Remove all* (areas) clear a list in one go, and Undo brings them back.
  - Undo covers the strata steps only. The outline in step 2 keeps its own Undo, as before.
- **Checked:** on the Delta plan, one click, drag, Draw wall line, Undo and Remove all (15 checks). 25-3402 re-run with the same figures as 1.41.23 on all three floors (TA 315.5 against 315.7). Building layout tests unchanged. Not yet opened in MicroSurvey.
- **To know:** on the Delta plan *Measure* read the outside walls on 7 of 14 sides and marked the rest assumed; those sides want a look before the plan is used. The outline there was set to the 14 corners from the screenshot (247.6 m² against 249.3 on screen), so areas on that plan are not a check of anything.

## Build 1.41.23 — 2026-11-16
- **Strata › One click follows the whole wall (change).** In 1.41.22 a wall that stepped sideways had to be clicked at each jog, which defeated the point.
  - **Now:** tap *Wall between lots* and click once anywhere on the wall. It's followed from one side of the building to the other, through door openings and sideways steps, and the strata line goes down its middle with the jogs put in square.
  - **A wall that passes through several lots cuts each of them.** One click on the basement suite wall of 25-3402 split both lots into their main part and secondary suite, with both 0.14 m jogs.
  - **Clicking a wall that's already in** adds nothing and says so.
  - **Where the plan doesn't shade the wall,** the one click can't follow it. The tool then asks for a second point along the wall, as before. *Wall with jogs* is renamed *Wall by hand* and is only for that case.
- **Checked on 25-3402 with one click per wall:** the same figures as 1.41.22 on all three floors (basement parts 49.4 and 55.7, Level 1 102.6, Level 2 107.8, TA 315.5 against 315.7 on the finished plan). The drawn test floor and Building layout re-checked. Not yet opened in MicroSurvey.

## Build 1.41.22 — 2026-11-16
Strata plan, worked through on a real job: the architect's set for 25-3402 (4144 Price Crescent duplex) checked against our finished strata plan for the same job.
- **Strata › Walls are read the way the plan draws them (change).**
  - **Shaded walls:** where the plan fills its walls (concrete, party walls), the strata line goes at the middle of the shaded part. A double stud wall with a gap is read as one wall.
  - **Wood-frame outside walls:** where the wall is lines only, the structural part is found behind the cladding and the strata line goes at the middle of the structure, not the middle of the whole wall. On Level 1 that put the line 0.125 m in from the outline, on a 0.154 m structure.
  - **Odd readings aren't trusted:** a side that reads very differently from the rest (a counter or stair beside the wall) takes the usual wall instead and shows dashed orange as assumed.
- **Strata › Wall with jogs (new).** For a wall that steps sideways, click at one end, at each jog and at the other end. Each straight run is centred on its own wall and the jog is put in square. *Wall between lots* is still two clicks for a straight wall; if those two clicks span a jog it says so instead of guessing.
- **Strata › Parts of a lot, notes and TA (new).** The wall tools also split one lot into parts. Give both parts the same lot number and they're added together in the floor table. Each part can carry a note (e.g. *Secondary suite*), and one floor of your choice shows each lot's total as *TA=*.
- **Strata › Pick outline takes the heaviest line under the click (change, Strata only).** On this architect's sheets that is the heavy line drawn round each floor, which gave a clean 12-corner outline on the basement and Level 1 with nothing to tidy. Building layout picks as before.
- **Strata › The DXF matches our strata drawings (change).**
  - **Layers** (still editable): `SL`, `SL ASSUMED (CHECK)`, `LCP`, `SL NH`, `SL_NO`, `AREA`, `DISTANCE`, `TEXT`, `TITLE`, and `A-WALL` for the picked outline.
  - **Lettering:** lot numbers as *PT. SL 1* at one and a half times the text height, areas as *49.5 Sq.m.*, notes and *LCP SL 1* / *NH* on TEXT, LCP sides dimensioned. Strata starts at 1:150 with Leroy 80 (0.30 m text) and remembers its own scale, separate from Building layout.
- **Checked against the finished 25-3402 strata plan** (figures there in brackets):
  - Basement: parts 49.4 and 55.7 m² each side (49.5 and 55.8).
  - Level 1: 102.6 m² (102.7). Level 2: 107.8 m² (107.7 by subtraction). TA 315.5 m² (315.7).
  - Dimensions agree within 2 cm (7.21, 7.49, 7.52, 7.35, 2.54, 1.70, 5.68, 3.35, 0.86, 2.46, 0.14, 13.33, 7.54, 3.40) except the suite wall's jog, which the tool places 6 to 7 cm along the wall from where our drafter did (3.75 / 3.76 against 3.82 / 3.70).
  - The DXF read back in an independent CAD reader with zero errors. Not yet opened in MicroSurvey.
- **Still not in this version:** LCP and non-habitable areas weren't run on this job (only on the drawn test floor); floors aren't lined up with each other; a picked area can't be edited.

## Build 1.41.21 — 2026-11-16
- **Building calc › Strata plan (new).** A switch at the top of Building calc, *Building layout | Strata plan*, turns the same tool into a floor-by-floor strata calc. It builds on the method from the Auto strata prototype (wall centre lines from both faces of the wall) and uses everything Building calc already has: PDF or CAD plans, the scale check, the automatic outline with its edit tools, Turn 90°, and each page's work kept.
  - **1 Scale and 2 Outline:** as for a building. Click the wall and the outline of the floor is followed; drop or redraw anything that isn't building (an attached deck or steps).
  - **3 Walls & strata lots:**
    - *Measure the walls from the drawing* finds the wall's second face beside each side of the outline and puts the strata line halfway. A side with only one face drawn uses the usual thickness you type and shows dashed orange as assumed, to check.
    - Strata lines can go at the wall centres or on the outer face of the outside walls, and **Side wall** sets any one side by hand (a thickness, or the outer face).
    - **Party wall:** click two points along the wall between two lots. Its other face is found, the line goes down the middle and the floor is split into lots. Lots are listed west to east with their areas; type the strata lot numbers and they're remembered for the next floor.
  - **4 Non-habitable areas:** *pick* (click inside a garage slab, sunken well or crawl space and its outline is followed from the drawing's lines) or *trace* its corners. An area drawn to a wall's face is carried on to that wall's strata line. Each lot shows total, non-habitable and habitable area.
  - **5 LCP:** the same pick or trace for decks, patios and porches, each assigned to a lot (the nearest by default).
  - **6 Floors:** save each floor (Basement, Main floor, Upper floor, or your own name) and go to the next page. A table shows every lot on every floor with the habitable total.
  - **7 Output:** no points file. *Strata DXF* has every saved floor side by side in metres: strata lines, assumed lines on their own layer, the wall's outer face, non-habitable and LCP outlines, lot numbers with areas, and each lot's sides to two decimals at the plot-scale lettering size. *Areas (.csv)* and *Summary* list the same figures. Layer names can be changed and are remembered (`CALC {date} STRATA LINES`, `… ASSUMED (CHECK)`, `… WALL FACE`, `… NON-HABITABLE`, `… LCP`, `… AREA`, `… DISTANCE`).
- **Not in this version:**
  - Floors are each on their own sheet coordinates, so there is no check yet that a strata line sits in the same place on every floor, and party walls aren't carried from one floor to the next.
  - A picked area can't be edited; remove it and pick or trace it again.
  - Garages aren't found automatically, and common property inside the building isn't handled.
- **Checked:** on a drawn test duplex floor (walls 0.150 m, party wall 0.250 m, a garage, a deck and a patio): the measured walls, both lots at 93.911 m², the garage at 19.331 m² held to the strata lines, the two LCP areas, two saved floors, the CSV and Summary, and the DXF read back in an independent CAD reader with zero errors. Building layout re-checked and unchanged. **Not yet tried on a real architect's plan or opened in MicroSurvey.**

## Build 1.41.20 — 2026-11-13
- **Building calc › Lot lines + calc (.dxf) replaces Our drawing + calc (change).** Bringing the whole lot drawing across made a mess on a full job file: on *24-2627-HOUSE-test* it carried 6,259 objects, including the sheet frames and title blocks drawn in model space.
  - **Now:** the file has only the lot lines from our drawing (the layer the lot was picked on, e.g. EX_LOT_LINES) plus the calc layers. No text, points, frames or anything else comes across.
  - **File name:** `…-LOT-LINES-WITH-CALC.dxf`. *DXF (calc only)* is unchanged.
  - **Checked on *24-2627-HOUSE-test*:** 11 lot lines on EX_LOT_LINES plus the calc, 56 objects instead of 6,259, about 10 KB instead of 2 MB. Read back in an independent CAD reader with zero errors and saved again. Not yet opened in MicroSurvey.

## Build 1.41.19 — 2026-11-13
- **Building calc › The small house plan on the Site view zooms (new).** On a building with many corners, the numbered *house as on the plan* was too small to read.
  - **Scroll** over it to zoom in on the spot under the cursor, **drag** inside it to move it, **double-click** to reset.
  - **Bigger / Smaller** (top-right of the box) switches it to a large version that covers most of the Site view.
  - Clicking a corner still fills the House box of the setback row. The lot drawing behind it doesn't move while you work in the box.
- **Building calc › Turn the house from the Site view (new).** The two **Turn house 90°** buttons are now on the Site toolbar as well, where the building is placed into the lot, and you stay on the Site view. It's the same quarter turn as on the Plan view: corner 1 becomes the south-west corner again and filled setback rows follow their corners.
- Includes everything in 1.41.18. That build went out three times under the same number, so browsers that already had it showed no update bar; this number makes the bar appear.
- **Checked:** zoom, pan, reset and Bigger on the test house; the turn from the Site view; and every 1.41.18 check again on this build.

## Build 1.41.18 — 2026-11-13
- **Building calc › Edit the excavation by hand (new).** Once the excavation is worked out, open the **Site** view to tidy it the way the excavator will dig it.
  - **Drop excavation corner:** click a corner, or drag a box round several. The side squares off to the **outside**, so a small jog beside a post becomes one straight side with a single corner at the end.
  - **Straight across (excavation):** click two corners and the ones between them go.
  - **Move:** drag a corner or the middle of a side of the dashed line; sides stay square.
  - **Undo last edit** in step 6, where the edits are listed. *Work out the excavation* asks before it clears them.
  - **The guard stays on.** An edit that would bring the line inside the distance off the foundation (4 ft), inside the post clearance (2 ft), or past the lot line is refused, and the message says which and by how much, e.g. *that would leave only 0.50 m (1'-7 3/4") off the foundation*. Where the lot line already holds the excavation short, that isn't counted against later edits.
  - The Summary lists the hand edits and the final corner count and area.
- **Building calc › Dimensions on every side of the building (new, on).**
  - **Text height from the plot:** in step 7, type the plot scale and the Leroy size. Leroy 80 at 1:250 gives text 0.508 m high (2.03 mm on paper). Both are remembered.
  - **What's drawn:** each side's length in metres to two decimals, centred on the side, parallel to it, outside the outline and never upside down. Long sides are placed first; a number that would sit on another number or on the outline is moved further out.
  - **In the files:** plain text on its own layer, `CALC {date} HOUSE DIMS`, in *DXF (calc only)* and *Our drawing + calc*. They also show on the Site view. Untick *dimension every side* to leave them off.
- **Building calc › Floor elevations block (new).** A new *Floor elevations* box under step 7 makes the **PROPOSED HOUSE** block for the crew's benchmark.
  - **Rows:** Main floor, Basement slab, Second floor, MBE and *Mechanical pump required*; rename them or add your own. Blank rows are left off.
  - **Typed or picked:** type the elevation, or press **Pick** and click its text on the architect's drawing (CAD text or PDF text; on a scan, or where the lettering is drawn as lines, type it).
  - **Both units:** an elevation in feet (76.92' or 76'-11") is shown in metres with the architect's figure in brackets, e.g. *MAIN FLOOR EL: 23.45 (76.92')*. One given in metres shows the one number. A picked number with no unit on the drawing is taken as metres, and the app says so.
  - **In the files:** the block goes inside the outline where there's most room, lettered along the building, at the same text height, on `CALC {date} HOUSE TEXT`. The same lines go in the Summary.
- **Building calc › Pick outline no longer doubles back through the inside (fix).** On plans where the outer wall has openings wider than the 1 m the pick joins across, the outline couldn't close round the outside. It came back through the inside instead: lines inside the building, a stop at a post, and corners stacked on top of each other.
  - **Now:** the pick measures how much of the outline is traced out and back along the same line. If it's more than half a metre, it joins wider gaps by itself (1.5, 2, 3, then 4 m) and keeps the first clean result. Step 2 says what it did.
  - **Checked on *ARCH_Final*, page 2:** at 1 m the outline was 98 corners and 324 m² with 111 m of it doubled. It now comes out at 78 corners and 607.6 m², joined at 2 m, with nothing doubled. Small leftovers such as a wall stub or a post box are still tidied by hand.
- **Building calc › Drop a side (new).** In **Drop corner / side**, click the middle of a side to take that side out: both its corners go and the sides either side join up square. Clicking a corner or dragging a box works as before. The same click works on the excavation in the Site view, with the clearance guard.
- **Building calc › Redraw a stretch (new).** Fixes one wrong part of a picked outline without starting over.
  - Click the corner where the outline stops being right, then the corner where it's right again. The stretch between them (the shorter way round) shows in red.
  - Click the true corners in between, in order; they snap to the drawing. With none, the two corners join up square. **Finish** (or click either end corner again) replaces just that stretch.
  - Every other corner stays where it was. *Undo last* and *Cancel* are on the hint line, and the whole edit can be undone with *Undo last edit*.
- **Building calc › Turn the plan to north (new).** Two **Turn 90°** buttons on the Plan toolbar turn the architect's plan a quarter turn either way, for sheets where the foundation plan isn't drawn north-up.
  - **Everything turns together:** the drawing, its lettering, a scanned page's picture, and anything already picked on it (scale marks, outline and its edits, posts, post lines).
  - **Corner 1 is the south-west corner again**, so the numbered house on the Site view reads the same way as the lot. Setback rows already filled in follow their corners to the new numbers; Calculate again afterwards.
  - It's for reading the plan, not for accuracy: lengths don't change, and the setbacks still work out the exact rotation. Four turns bring it back exactly as it was. Each PDF page keeps its own turn.
- **Building calc › Changing the page no longer loses your work (fix).** Each PDF page's scale, outline, edits, posts, setback rows and excavation are kept while the file is open. Go back to a page and it's as you left it. A page you haven't worked on still starts clean. The floor elevations stay with the file, so you can go to the site plan or a section to pick them and come back.
- **Building calc › The drawing's own lettering shows on the Plan view (fix).** On PDFs with real text (e.g. *ARCH_Final*, page 2) the dimensions and notes didn't show, only the linework. They now appear once you zoom in far enough to read them, and CAD text shows the same way. Large watermarks such as DRAFT stay faint.
- **DWG files the reader can't open now say so (fix).** A drawing that crashed the in-browser DWG reader showed only *memory access out of bounds*. The message now says it's the reader, not your file or drive, and to save the drawing as DXF from MicroSurvey and drop that. The reader also starts fresh for the next file. Applies to Building calc and Coordinate design.
- **Checked:**
  - Excavation edits on a test house with a post on the 4 ft line: click, box and straight-across drops, drags, undo, and each kind of refusal (foundation, post, lot line).
  - The DXF read back in an independent CAD reader with zero errors: 6 dimensions and the 6-line block at 0.508 m, on their layers, and saved again.
  - Page memory and the lettering preview on *ARCH_Final* (pages 2 and 3).
  - Drop a side and Redraw a stretch on the *ARCH_Final* outline, each undone cleanly.
  - Turn 90°: side lengths and area unchanged, corner 1 at the south-west, setback rows renumbered with their corners, and four turns back to the start exactly.
  - Not yet opened in MicroSurvey, and the DWG message couldn't be tried on *QUALTROUGH_ARCH_V13.dwg* itself.

## Build 1.41.17 — 2026-11-12
- **Building calc › Our drawing + calc (.dxf) saves cleanly in MicroSurvey (fix).** The 1.41.11 version opened in MicroSurvey CAD 2027, but saving failed with *Error 314 (Unknown internal error during save)*. It was built on the modern DXF that the app's DWG reader makes from your drawing, and MicroSurvey couldn't save that back out cleanly.
  - **Now:** the file is written in the same plain format (R12) as *DXF (calc only)*, which MicroSurvey already handles. It carries your drawing's lines and polylines, circles, text and points on their own layers, with the layer colours from your drawing, plus the calc layers.
  - **Left out:** frozen or off layers, hatches, and dimension objects. Blocks come through as their linework.
  - **Points:** MicroSurvey's point database is still the points file. Import the calc's Points (.txt) for real MicroSurvey points.
  - **Checked** on *26-3657-House-test*: 1,174 objects across 17 layers (including the 18 lot lines on EX_LOT_LINES). Read back with zero errors, and saved again without trouble.

## Build 1.41.16 — 2026-11-12
- **Building calc › Excavation round posts the way it's dug (change).** Posts beyond the 4 ft line used to get a narrow finger of excavation each.
  - **Now one rectangle per side:** posts on the same side are taken in together by squaring off that side of the excavation, 2′ clear past the posts.
  - **Lined up with corners:** the rectangle is widened to line up with the excavation's own corners within 3 m.
  - **Unchanged:** a post sitting on the 4 ft line still gets a box round it.
  - **The note** lists the posts and how far beyond the line each was.
- **Building calc › Simplify the excavation (new, on).** The excavation no longer follows every small jog in the house wall. Inward steps up to **1.25 m** (editable, tick-box in step 6) are filled so the sides run straight, like a hand-drawn excavation. Deeper real steps stay, and it's still held to the lot line.
- Matches the examples from *26-3657* (posts below the house, cyan) and *1516 Kerfoot Road*.

## Build 1.41.15 — 2026-11-12
- **Building calc › Edits stay put (fix for the "endless cycle").**
  - **Before:** every edit (drop corner, box drop, straight across) re-ran the whole outline process: squaring every wall, ¼″ rounding from corner 1, the opening and door tidy-ups, and renumbering from the south-west corner. Each edit could therefore shift or renumber corners elsewhere.
  - **Now:** edits only change the spot you touch. Every other corner stays exactly where it was and keeps its order, and the outline stays square. Tested on Kerfoot page 3: a box drop, a single drop and a straight-across left all other corners unchanged.
- **Undo last edit (new).** A button in step 2 steps back one edit at a time (drops, straight across, corner and side drags).
- **Asks before starting over.** Changing a tick-box (rounding, jogs, door swings, fill openings), the gap or the layers, or picking again, works the outline out again from the drawing. Once you've made edits it now asks first, and says how many edits would be cleared.
- **Fix:** a click where there's nothing to follow could stop the pick with an error, so nothing happened. It now says it couldn't close an outline there.
- **Checked against your 1.41.10 export** (*1516 Kerfoot Road-p2-CALC.dxf*, 14 corners, 306.76 m²). On page 2, 1.41.10 and this build make the same first pick, 18 corners and 345.7 m². Your export is that outline with the window well and the patio slab taken out.

## Build 1.41.14 — 2026-11-12
Worked through on *1516 Kerfoot Road*, page 3 (main floor). Its west wall has two garage doors, two entries, windows and boxed-out columns. The outline came out with 75 corners; it's now 24, all square.
- **Pick outline follows the black wall lines, not coloured overlays (fix).**
  - **The cause:** on sheets with the floor above drawn in orange (*Flr Above*), the pick could start on an orange line and follow that layer. That was the jogging inside the outside wall.
  - **The fix:** on PDFs, coloured lines near the click now lose to black or grey wall lines, and the search looks a little wider before choosing.
- **Fill in openings (new, on for PDFs).**
  - **What it does:** at windows, doors and garage doors the pick dropped onto the frame line, a wall's thickness in, and came back out. Where the outline steps in from a wall face and back out onto the same line, no deeper than 0.45 m and no longer than 10 m, it's now straightened along the face.
  - **What stays:** real recesses deeper than that, like a recessed entry, are left.
  - **Off by default for CAD files**, where wall geometry is exact. A tick-box in step 2 turns it on or off. Step 2 says how many were filled, and the readout includes it.
- **Door-swing cut closes along the walls, never on a diagonal.** It now follows the walls either side: straight on if they're in line, the square corner if they meet, a square step if they're offset. The limit is now 3 m, which covers double doors.
- **When an outline won't close, it tries wider gaps by itself.** It retries at 1.5, 2 and 3 m and says what was needed (Kerfoot page 3 needed 1.5 m). *Join gaps up to* is now in step 2 before the first pick as well, not only after one has worked.
- No change on the A214 DWG (34 corners, 221.09 m²), D2609 PDF or Kerfoot page 2 (18 corners); 25-3402 placement still reproduces the office calc.

## Build 1.41.13 — 2026-11-12
- **Building calc › Door-swing cut limited to door openings (fix).** In 1.41.12 the cut could replace whole lengths of wall with one long diagonal, e.g. along a side drawn slightly off square with small steps. It now only cuts a run that spans **2 m or less**, the width of a door opening. Anything longer is left exactly as picked. The mocked door is still cut cleanly. A214, D2609 and Kerfoot are unchanged.

## Build 1.41.12 — 2026-11-12
- **Building calc › Outline tidy-up back to the earlier defaults.** *Take out jogs under 20 mm* is on again and corners round to **¼″** again, as before 1.41.8. With both off, plans with lots of small steps came out with crowds of corners. Both are still tick-boxes, and *Largest difference from the drawing's lines* still shows what the tidy-up costs (A214: 12.2 mm, from one 13 mm jog).
- **Building calc › Door swings cut straight across (new, on by default).** A door leaf and its swing arc drawn in the same pen as the wall, and touching the jamb, were followed as part of the foundation. Now any run of off-angle sides between square corners that contains an angle other than 45° (a leaf plus an arc) is replaced by a straight line across the opening, then squared. Runs that are all 45° (bays, chamfers) are left alone, and so are square jogs. Step 2 says how many were cut; there's a tick-box to turn it off. No false cuts on the A214 DWG, the D2609 PDF or Kerfoot page 2.
- **Building calc › Drop several corners at once (new).** In *Drop corner*, drag a box round the corners you don't want and they all go in one step (a click on a single corner still works). The edit lists which corners went.

## Build 1.41.11 — 2026-11-11
- **Building calc › Excavation takes in the posts (fix).** A post more than 4′ + 2′ from the house was left outside the excavation, because its clearance square came out as a separate piece and was dropped. The excavation now runs out to take in any post beyond the 4 ft line, at least 2′ clear round it, held to the lot line as before. The note says how far beyond the line each post was.
- **Building calc › Excavation distances read the way you type them (fix).** A plain number is metres, so *4* and *2* meant 4 m and 2 m, and *4 ft* wasn't understood at all.
  - **Accepted now:** 4', 4 ft, 4ft, 2 feet, 48in, 4' 6", 1.219, 1.219 m.
  - **Shown back:** each box shows what it was read as (*= 1.219 m (4'-0")*).
  - **Warning:** a plain number that's large for metres (over 2.5 m off the foundation, or over 1.5 m clear of posts) gets *4 metres? For feet type 4'*.
- **Building calc › DXF layers pre-filled with today's date, posts on the house layer.**
  - **Shown in full:** the layer boxes show the real names with today's date, e.g. *CALC 26-11-11 NEW HOUSE*. They're remembered with the date as a placeholder, so tomorrow they show tomorrow's date.
  - **Posts and post lines** go on the NEW HOUSE layer by default; post lines are still dashed. Separate post / post-line layers are under *Separate layers for posts / post lines*. Names saved under the old POSTS / POST LINES defaults switch to the new ones.
- **Building calc › Our drawing + calc (.dxf) (new).** A copy of our own lot drawing with the calc added:
  - **Everything kept:** every object in it is kept as it was. The calc goes on its layers, which are added to the drawing's layer table with fresh handles, and the drawing's own format is kept.
  - **Tested** on *26-3657-House-test*: all 2,686 objects kept, 77 added, read back with zero audit errors.
  - *DXF (calc only)* is still there for the calc on its own.

## Build 1.41.10 — 2026-11-11
- **Building calc reads the point numbers in our own lot drawing.**
  - **Where they come from:** MicroSurvey stores each point's number on the point itself, and the app now reads it. Drawings without that fall back to the point-number label beside the point.
  - **Lot corners named:** corners now carry their real point numbers without a points file on the shelf. On *26-3657-House-test*: 2, 1, 6, 10, instead of L1–L4.
  - **No clashes:** new house, post and excavation points are numbered clear of the job's points file *and* the lot drawing's points. 26-3657 starts at 1100: the drawing already uses 1–15, 50, 100–114, 210–215, 250–254 and 1000–1004.
  - **Check in step 7:** it says how many points were checked (shelf + lot drawing). If a start number you type would reuse a number, it lists the clashes and offers *Use … and up*.
- An MSZ or points file on the shelf still counts as well.

## Build 1.41.9 — 2026-11-11
- **Building calc › See the house's corner numbers while you enter setbacks.** The Site view now shows a small **plan of the house, as on the architect's plan, with every corner numbered**, top-right. The numbers in the row you're working on are highlighted.
- **Fill setbacks by clicking.**
  - Click a numbered corner on the small plan to fill **House** (a *pair ∥* row takes two corners in turn).
  - Click a lot side on the drawing to fill **Lot side**. Lot side labels are bolder once the lot is confirmed.
  - The cursor then moves to the setback box for you to type the distance.
  - Clicking into a box first fills that box; otherwise the next empty one is filled, and a new row is added when they're all full.

## Build 1.41.8 — 2026-11-11
- **Building calc › The outline stays on the drawing's lines (accuracy).**
  - **New readout:** step 2 now shows *Largest difference from the drawing's lines*: the furthest any corner or side of the outline is from the linework it was picked from. Green at 2 mm or under, amber over. A breakdown shows what caused it (squaring, jogs taken out, rounding); your own edits aren't counted.
  - **Rounding:** corners now round to **1/16″** (at most about 1 mm), not ¼″, which could move a corner up to 3.2 mm where the plan is dimensioned in eighths. It's still a tick-box.
  - **Jogs:** *take out jogs under 20 mm* is now a tick-box and **off by default**. On the A214 plan it had removed a real 13 mm jog, 12 mm off the drawing.
  - **Result:** A214 DWG outline within **0.5 mm** of the drawing (was 12.2 mm); Kerfoot PDF page 2 within 0.0 mm. 25-3402 placement unchanged (setbacks 1.377 / 13.401 / 1.781 reproduced, rms 0.01 mm).

## Build 1.41.7 — 2026-11-11
- **Building calc › Draw post line snaps (fix).** It only snapped quietly to post centres and outline corners, with nothing on screen to show it. It now has the same green-square snap marker as Measure, labelled with what it found:
  - **post centre**, **post corner**, **house corner**
  - **corner / end** and **crossing** in the drawing
  - **perpendicular:** once the first end is placed, bring the cursor near a house wall and the second end snaps to the point square to it. A post line from a post back to the house is therefore exactly perpendicular.
  - A dashed line runs from the first end to the cursor with its length. The *Snap* switch turns it off.

## Build 1.41.6 — 2026-11-11
- **Building calc › Our lot drawing showed blank (fix).** A lot drawing with stray objects far from the lot opened zoomed out so far that the lot was a dot. Examples: a control point at real coordinates while the lots are local, or the sheet frame drawn elsewhere in model space. The Site view now fits the **lot-line layer** (EX_LOT_LINES or the one you pick), and *Whole drawing* skips far-off strays. Checked on *26-3657-House-test.dwg* with *1516 Kerfoot Road* page 2: the lots show, a click inside one picks it (22.43 × 39.72 m, 890.21 m²), and the fit and excavation run.
- **Building calc › Setbacks warn when the house lands over the lot line.** If the fit puts any house corner outside the lot, step 5 names those corners and says to check each row's lot side and house points. A setback measured from the wrong side is the usual cause.

## Build 1.41.5 — 2026-11-11
- **Building calc › Drag the outline to adjust it, before or after confirming.** In *Move* on the Plan view:
  - **Drag a corner:** both sides at that corner follow and keep their direction, so it stays square.
  - **Drag the middle of a side:** the whole wall slides in or out, parallel. Use it to move a side onto the outer face of the wall, or back off a post it took in by mistake.
  - Drags snap to line corners (green square), and the cursor changes over a corner or side. Each move is listed under *Edits* with how far it went.
  - **On a confirmed outline,** a drag, *Drop corner* or *Straight across* asks you to confirm it again. Posts, the lot and your setback rows are kept. Check the corner numbers in the setback rows (Drop corner / Straight across can renumber), then Calculate and work out the excavation again.
- **Building calc › Posts, by hand.**
  - **Pick post:** click inside a post. This now works when it's drawn as four separate lines, not only as one closed shape (grid and annotation lines don't count). Click a post again to take it off.
  - **Post by corners (new):** click one corner, then the opposite corner (both snap). The post is squared to the building, and a dashed box shows it as you go. It also works where the post isn't drawn as a closed shape.
  - **Post line to house (new):** click a post and a dashed post line is drawn from its centre square back to the nearest wall of the outline. **Post lines from every post to the house** does them all at once. *Draw post line* (two clicks) is still there for anything else.
  - Posts drawn by corners keep the building's angle in the DXF and in their corner points.

## Build 1.41.4 — 2026-11-11
- **Building calc › Snap you can see.** In Measure and Trace outline, a **green square** follows the cursor when it's on a line end or corner (labelled *corner / end*), with an ✕ in it on a crossing of two lines. Off a corner, a small grey + shows where a click will land. A click lands exactly where the marker shows. **Snap** switch on the toolbar (on by default, remembered) to turn it off; there's nothing to snap to on a scanned page.
- **Building calc › Measure shows where you are.** The first point gets a numbered **①** marker and the second **②**. Between clicks a dashed line runs from ① to the cursor with its length (m and ft-in once a scale is set). The hint above the drawing and step 1 say *① is placed — now click the second end ②*, then *① and ② are placed — type the length*. Dragging an end snaps as you move it. Trace outline also shows a dashed line from the last corner to the cursor.

## Build 1.41.3 — 2026-11-11
- **Building calc › Pick outline on PDFs drawn with plain lines (fix).** On plans where the walls are double lines with no fill, and the dimensions and lettering are in the same pen (e.g. *1516 Kerfoot Road*, page 2), the pick tried to follow the whole sheet and the page stopped responding. It now leaves out lettering and other bits under 0.3 m across, and only joins gaps between real pieces of wall. It never runs away: if a layer is too busy it stops and suggests Trace outline. *Following the outline …* shows while it works. Kerfoot page 2 now takes about 0.2 s and follows the exterior walls (18 corners). Tidy the window well and the patio slab drawn below with *Straight across* if they aren't part of the foundation.
- **Building calc › Trace outline (new).** Click each outside corner in turn; on CAD and vector PDFs each click snaps to line corners. Click corner 1 again, or *Finish*, to close; *Undo last* takes a click back. The traced outline is squared and edited like a picked one.
- **Scanned pages:** Building calc now shows the scanned page as a picture behind the viewer. You can Measure for the scale and Trace the outline on it (nothing to snap to, so check a couple of dimensions). Pick outline is greyed out on a scan.
- **After the scale is set, the tool switches to Pick outline** (Trace on a scan), so clicks no longer keep measuring.
- **PDF page guess:** goes to the page with the biggest *FOUNDATION PLAN* title, not the drawing list (D2609 now opens on page 6, not the sheet index on page 4).

## Build 1.41.2 — 2026-11-11
- **Building calc › Measure: move the markers (fix).** A + put down in the wrong place couldn't be moved. Hover over either end (the cursor changes to a move cursor) and drag it; it snaps to line ends when you let go. *Clear* in step 1 removes both. Clicking elsewhere still starts a new measurement.

## Build 1.41.1 — 2026-11-11
- **Points › Coordinate design / Building calc without a points file (fix).** A drawing dropped on the Points tab with no points file on the shelf opened in Coordinate design with no way to reach Building calc. The two tools now show as tabs there too.
- **The dropped drawing goes with you.** Switching between Coordinate design and Building calc loads the drawing you dropped into the one you switch to (unless it already has it). This works with or without a points file.
- **Scanned PDFs are said plainly.** A page that's a scanned image has no lines or text to read. Both tools now say so and ask for the CAD file or a PDF printed straight from CAD, instead of *No design bubbles on page …*. Example: *Duplex Arch+Str.pdf* is 18 scanned pages.
- **Building calc opens a PDF on its foundation plan page** when the sheet titles are text (otherwise the basement plan, otherwise page 1).

## Build 1.41 — 2026-11-11
- **Points › Building calc (new tool).** Works out a new building from the architect’s plan, one step at a time. Each step opens once the one before it is confirmed. Plans in feet and inches are fine; **everything that comes out is metric** (ft-in shown alongside). If the set has both a foundation plan and a basement plan, use the foundation plan.
  - **Drawings:** the architect’s .dxf, .dwg or vector PDF (with a page box for the sheet). Drop it on the Points tab while you’re in Building calc, or use the button.
  - **1 Scale.** CAD files offer their own units (*Use them*). PDFs offer the common sheet scales (1/8″, 3/16″, 1/4″, 3/8″, 1/2″ = 1′-0″, 1:50, 1:100, 1:200). Either way you can **Measure**: click the two ends of a dimension you trust and type its length (24′-6″ or 7.468). The scale is checked against the dimensions on the drawing (*52 of 52 agree*), and any that don’t agree are listed.
  - **2 Outline.** *Pick outline*, then click the foundation wall or inside it. The outline is followed round on its own, including walls drawn as hatches (Revit) or grey fills (PDF), and joined across openings up to 1.0 m (editable). It is then **squared to the building axis**: 0 / 90°, 45° where drawn that way, and any other angle left as drawn and flagged. You’re told how far anything moved. Corners are rounded to ¼″ on imperial plans (a tick), and drafting jogs under 20 mm are taken out. Side lengths are listed in m and ft-in. Edits: **Drop corner**, and **Straight across** (click two corners; the ones between, the shorter way round, go). The layers it followed are ticked, so you can change them and *Pick again*. Corners are numbered 1… clockwise from the south-west corner of the plan.
  - **3 Posts** (or *No posts*). *Pick post* (click one), then **Select similar** finds the rest; click one again to take it off. **Draw post line** adds dashed lines (snaps to post centres and outline corners). Points per post: centre, or centre + corners.
  - **4 Lot.** Load **our own CAD file** with the calculated lot lines (.dxf / .dwg) and click inside the subject lot. Corners are named with the job’s point numbers when its points file is on the shelf (otherwise L1, L2 …). **Arcs are read** with their radius (and radius point number when it’s on the shelf). Or tick **No lot — local coordinates only**: corner 1 at a chosen E / N, plan orientation (or rotated).
  - **5 Setbacks** (only once the lot is confirmed). Each row is a **house point to a lot side** (e.g. 1 → 2–3 at 1.500), or a **pair of house points parallel to a lot side**. Distances are in m or ft-in, and sides can be arcs. **Calculate** fits the house: exact with two or three rows, a best fit with more (rms shown). *Got* shows each setback achieved against what was asked. If the house can still slide, it says which way, so you know what setback to add.
  - **6 Excavation.** 4′ off the outline (editable) and at least 2′ clear of any post (editable), **held to the lot line** (arcs followed). Notes say where it was held and where a post is left short. It’s measured from the outline you confirmed: if the office measures from the footing, add the footing’s projection.
  - **7 Output.** Points numbered **1–99** when the job’s file leaves them free, otherwise from the next clean hundred above it (editable): house corners, posts, then excavation corners (*CALC HOUSE / CALC POST / CALC EXC*). Points file (.txt, PNEZD), DXF and summary. **DXF layer names are yours and remembered**: defaults `CALC {date} NEW HOUSE`, `CALC {date} HOUSE PTS`, `CALC {date} POSTS`, `CALC {date} POST LINES` (dashed), `CALC EXCAVATION`, `CALC EXCAVATION_PTS`, where {date} = YY-MM-DD.
  - **Tested on 25-3402 (4144 Price Cres):**
    - A214 foundation plan DWG: 52 of 52 dimensions agree and the outline is 221.1 m². On the PDF (page 6, 1/4″) it is 220.2 m².
    - Fitted into lot 4 with the office calc’s setbacks (west face 1.377, lane 13.401): it lands on the office calc’s corners (median 0.6 mm). The east side comes out at 1.781 m, the same as the calc.
    - The east stair-well notch and the stair walls on the west are drawn deeper on the plan than in the calc. Use *Straight across* / *Drop corner* to match how the office simplifies them.
    - The office’s excavation ran about 0.17 m further out than 4′ from the calc outline (≈ 4′6½″, likely measured from the footing).
- **Points tools grouped.** The row of tools is now three groups, each showing what’s inside:
  - **Clean up a topo:** Clean-up · Tree table · Height check
  - **Scale & move points:** Scale · Match points · Transform
  - **Design & stakeout:** Coordinate design · Design vs Field · Building calc · Monitoring
  - A line under the tools says what the open one does.
  - The last group and the last tool in each group are remembered.
  - A drawing dropped on the tab opens in Coordinate design, or in Building calc when you’re in it (the plan first, then our lot drawing).
- **Coordinate design:** the DXF layer name is now an editable box under the outputs, remembered. Default `CALC {date} DESIGN PTS`, with the date now written YY-MM-DD like your other CALC layers (was YYMMDD). Nothing else about Coordinate design changed. Its outputs were checked identical to 1.40 on the 21-016 DXF and the 21-203 PDF.
- **Training:** *Design vs Field — cut / fill example* (Elevate office app folder) is now linked in Training and on the Design vs Field tool. Building calc links *House calc for new subdivision (Delta)*. Every other video in the Training Videos library was already linked.

## Build 1.40 — 2026-11-10
- **Points › Coordinate design (new tool).** Coordinates the engineer’s design elevation bubbles so the crew can stake cut / fills. Drop the drawing on the Points tab (or use the button in the tool). A points file isn’t needed, but one on the shelf sets the numbering and lets you place a PDF by point number.
  - **Drawings it reads:** the engineer’s CAD file (.dxf, or .dwg, which is converted on the fly) or a **vector PDF** plotted from CAD. Scanned PDFs can’t be used.
  - **Bubbles are found by their shape:** an oval holding an elevation (or MEET) with a leader. The point is the **end of the leader**, or the centre of the x / tick / + there. Layer and block names don’t matter, so any engineer’s drawing works. The layers they were found on are listed.
  - **PDFs:** the numbers in a plotted PDF are pen strokes, not text, so the tool reads them itself. Anything it isn’t sure of is flagged for you to check; nothing is guessed silently. When you correct a value it **learns that engineer’s lettering**, and *Re-read with what it’s learned* fixes the rest.
  - **Bubbles drawn twice:** a bubble drawn twice on top of itself is spotted. The one on top is used, and it's flagged when the copy underneath reads differently or its leader points somewhere else (*Use the leader underneath* swaps them).
  - **Placement:** CAD files are used as drawn (or pick matching points, rotation + shift). A PDF is placed with the **underlay values** from MicroSurvey (insert E / N, metres per sheet mm, rotation) or by **picking matching points** and typing their point number or N, E. Residuals are shown.
  - **Viewer:** move / zoom, *Select bubbles* (drag a box; Shift removes), *Pick line* (click the gutter, centreline or swale and it’s followed to its ends, across dash gaps), *Pick point*. Colours: found, selected, flagged, confirmed, dropped, MEET, curve point.
  - **Checking:** *Select bubbles on the lines*, then confirm one by one (✓) or *Confirm all with nothing flagged*. Type over a value to correct it. ✕ drops one with a reason (lot / building corner, off the line, duplicate…). Each bubble shows its distance from the line. Anything beyond the on-line tolerance (default 0.05 m), up to 0.5 m, is flagged *not on the line*.
  - **MEET** bubbles are left out by default. A tick includes them horizontal-only (elevation 0, never a cut / fill).
  - **Curves:** on each picked line the curves are found from the linework (CAD arcs exactly; plotted curves from the drawing’s own joints, dashed lines from a fitted circle). BC, MC and EC get interpolated elevations, linear by distance along the line between the design values either side. A curve point within 0.5 m of a design point is skipped. A closed island wraps round. Tick off *Interpolate* to leave them out.
  - **Long stretches** with no design point (default over 30 m) are listed with their grade, to check before staking.
  - **Numbering:** design points from the next clean thousand above the shelf’s points (e.g. 6004 → 7001), in line order along each line (⇄ reverses a line). Curve points come from their own block (7201…) with *INTERP* in the description. Descriptions are the line name (GUTTER, CL…), or SWALE INV / TW / BW where you tag one.
  - **Outputs:** points file (.txt, PNEZD), points for the drawing (.dxf, POINTs plus number / elevation labels on their own layer), a summary (.txt: placement, lines, what was confirmed, corrected and dropped and why, curve points with the values they came from, long stretches). All stay locked until every selected bubble is confirmed or dropped. *Send to Design vs Field* puts the points on the shelf and passes the lines across.
- **Points › Design vs Field › Stakes to line (new).** Offset stakes and stakes between design points.
  - Field points that aren’t paired with a design point are measured to the line: station, **offset (L / R looking along the line)**, and **cut / fill to the design elevation on the line** at that spot (interpolated between design points, marked *). It’s never the grade at the stake itself.
  - The lines come from Coordinate design (with their true curves) or from design point ranges (*7001-7026; 7027-7110*, joined in point-number order). Max offset defaults to 3.00 m.
  - Stakes get descriptions like **2.00R C0.12** (the existing switches still choose horizontal / cut-fill). They have their own table on screen, in the .dxf (beside the paired table) and in Copy table. A field point at a corner, where two places on the line are equally near, is noted.
  - Paired stakes are unchanged (e.g. *FILL0.10 0.004N 0.006W*).
- Points tab: the drop zone and *Choose file* also take .dxf / .dwg / .pdf, which open in Coordinate design.
- **Points › Design vs Field › Description (new choice).** What the stakes' descriptions become in the amended points file:
  - **Add to existing**, as before (the default): `GUTTER --Replaced point ID Stkd7034 FILL1.31`.
  - **Replace with the result only:** `FILL1.31`. Use it when the existing description is no longer relevant, e.g. MicroSurvey's *--Replaced point ID…* note.
  - **Replace with design description + result:** `GUTTER FILL1.31`. This takes the paired design point's description; a stake set to a line takes the line's name.
  - Point numbers, coordinates and every other line are untouched, as before. The example line under the switches shows the result.
- **Points › Design vs Field › Include › Design point number (new switch).** Puts the design point the stake was compared to at the front of the result, e.g. **STK 100 CUT0.05**. It works with any Description choice; with *Replace with the result only* the description becomes exactly `STK 100 CUT0.05`. Stakes to a line (between design points) have no single design point, so they keep the offset and C/F only. The design point number was already the first column of the .dxf table.

## Build 1.39.2 — 2026-11-05
- **Points › re-dropping an edited file now refreshes every tool (fix).** Dropping a corrected file again under the same name (e.g. 26-3670-SITE.msz after fixing the tree shots) used to leave the Height check showing the old points until the page was reloaded.
  - **Height check:** re-reads the points straight away and keeps the drawing you picked, the units, the limit and the ground layers. A line says the file was dropped again and re-read.
  - **Design vs Field, Monitoring, Match points:** re-run by themselves with the same ranges, base and settings when they had a result from that file, and say so.
  - **Clean-up, Tree table, Scale, Transform:** already read the new copy; checked.
  - Switching between packages on the shelf: the Height check now reads each package's own points (with its drawing handles), not just the last one dropped.
- **PM › Disbursements:** more than one *Other*.
  - **+ Add another** adds a row; ✕ removes one; empty rows are ignored.
  - Every Other counts in the totals. Each is listed with its amount on the Word quote and in the job details file (one entry each), and read back from it.
  - An older quote's single Other becomes the first row. Quotes saved here still open in older builds (they see all Others joined as one).
  - Sub-quotes and *Start from a past quote* start with none.
- **PM › Services: drag to reorder.**
  - Grab a service by its **⋮⋮** handle (left of its number) and drag it up or down. A line shows where it will land and the page scrolls near the edges.
  - Esc, or letting go away from the list, cancels.
  - The ↑ ↓ arrows still work. Either way the whole service, with its wording and hours, moves.
- **Points › Monitoring follows the job's own spreadsheet.**
  - **New points:** shots in the trip's point range that don't sit near any base point are listed by number and description — *new monitoring points, or other shots?* (On 22-1740, J and K were shot for weeks before anyone noticed.)
  - **Three copy buttons:**
    - *Copy changes* — as before (ID + ∆N ∆E ∆Ele, ∆Total if ticked).
    - *Copy averaged coordinates* — each point's averaged N / E / Ele in the columns of the header you pasted (e.g. Desc. | N | E | Ele | Location). Point numbers are included if your header has a Point column; Location is the shot's description without "-CHK". For sheets whose own formulas work out the changes.
    - *Copy shots* — every shot used (Point, N, E, Ele, description, ID) in point order, then "Average Coordinates" and the averages — for a field-day sheet.
  - A note says the changes are observed − base; some workbooks (e.g. 22-1740) use base − reading, so there you'd paste the averaged coordinates.

## Build 1.39.1 — 2026-11-04
- **PM › Previous quotes at this address:** when the address hasn't been quoted before, a faint line now says so, e.g. *✓ Checked: not quoted before (Elev_Quotes_Master, 4,955 quotes)*. You can tell the check ran.
- **PM › Jobs › Approval date:** stays today's date. Before, it was set once when Jobs first opened, so a tab left open overnight still showed yesterday (and named the approval folder for yesterday). It now resets to today when Jobs is shown and again just before the folder is made. A date you pick yourself is kept; clearing it goes back to today.
- **PM › Jobs › Quote #:** the quote folder is found by itself. Once a full quote number is typed (26-597, 26-597B), it searches after a short pause or when you leave the box. Enter still works.
  - Typing a different number clears the old folder straight away, so the wrong quote never stays on screen.
  - The button reads *Search again* once a folder is found.
  - If the browser needs your OK to read the folders, the button waits for your click; it never asks by itself.
- **PM › Older Word quotes** (not made in the app) — kept simple:
  - *Open a quote* (and *Start from a past quote…*) now copies the **header** — date, client, Quote #, site address — and each service's **sub-items as written**: the heading, the lead line and the bullet lines.
  - A service gets a library type only when its heading clearly names one (e.g. *Topographic Site Plan…* → topo).
  - Prices, disbursements and hours aren't copied. The Project Manager is yours, it's **NOT SAVED** until you save it, and one line says what was copied.
  - On the Jobs view, dropping an older Word quote fills in its Quote # and client.

## Build 1.39 — 2026-11-02
- **PM › Start from a past quote…** (new button beside *Open a quote*). Pick a past Word quote (made in the app) or its job details .txt to use as the sample for a **new** quote.
  - Tick what comes across: **Site details** (address, legal, PID, plans, zoning, project line, extra properties), **Services and wording** (with the field crew instructions and rate-sheet option), and **The sample's hours** — off unless you want them, so hours start at zero.
  - Two quick choices: **Use as a sample** (services only) and **Same site, new client** (site + services).
  - Never brought across: client, contact, email, phone, Quote #, date requested, PM comments, notes, Services Provided and task details, scope pages, prices and per-unit prices, disbursements (back to $0).
  - Dollar amounts typed into the wording are blanked to **$___** and the line marked red. Wording that is word-for-word the current approved library wording keeps its standard amounts.
  - Project Manager and initials stay yours. It's a new quote (not a sub-quote), **NOT SAVED** until you save it, and the past quote's file is never changed.
- **PM › Previous quotes at this address.** Under each site address, next to the research buttons: *Quoted before: 24-165 (client, year)*.
  - Read from **Elev_Quotes_Master.xlsx** in your connected *Quotes - Documents* folder, re-read whenever it changes. Only that exact name counts; dated backups are ignored.
  - Also checks **To Do Quotes.xlsx** in the same folder, labelled *in To Do Quotes (not in the master yet)*. If it's missing or can't be read, it's skipped quietly.
  - Matched on civic number + street name: case, unit / suite / #, punctuation, St / Street, Ave / Avenue, W / West, 20 / 20th are ignored. The city keeps same-named streets in different cities apart.
  - The quote you're on and its sub-quotes aren't listed. Not shown on sub-quotes.
  - Click a number to copy it (paste into File Explorer's search). **Start from this one** finds that quote's Word quote or job details file in its folder and opens *Start from a past quote* with **Same site, new client** ticked.
  - If the browser needs your OK to read the folder again, a **Check previous quotes at this address** button asks once.

## Build 1.38 — 2026-10-30
- **Points › Height check works on feet drawings.**
  - A **Metres / Feet** switch sits beside the limit. It's picked from the drawing's own units (or from UTM-in-feet coordinates) and says where it came from; change it any time.
  - In feet, the limits are round foot values: flag at **1.0 ft**, look **80 ft** around each point, same-spot shots **0.3 ft** apart. All still editable.
  - Contours are **1 ft by default** on a feet drawing (2 ft, 5 ft or off).
  - Everything reads in feet: "11.95 ft lower than all 4 points around it", the point details, the legend and **Copy list** (Elev (ft)). Your points and drawing are never converted.
  - Metric drawings are checked exactly as before (26-3582: the same 30 flags).
- **PM › ALR button** under each site address, next to BC Assessment. It opens the Agricultural Land Commission's *Is My Property in the ALR?* map and copies the **PID without dashes** (the way that map's search wants it), or the address when there's no PID. Not on sub-quotes, like the other research buttons.
- **Resources:** *Is My Property in the ALR? (ALC)* added under Provincial / federal.
- **Training:** three new videos.
  - *Height check (Points tab)*, also as the ▶ Training link on the Height check tool.
  - *Pasting a tracker row* (PM tab).
  - *Topo + posting + new construction + strata sample (multi-service)* (PM tab).

## Build 1.37 — 2026-10-28
- **Points › Height check** (new tool button), to catch topo heights that are too high or too low before the drawing goes out.
  - Load the topo's **.msz** in the Points tab as usual, open **Height check**, then **Add drawing (.dwg / .dxf)**.
    - Every point is matched to the drawing exactly, by MicroSurvey's own link between the two.
    - The layer that counts is each point's **elevation text** layer.
    - The DWG reader loads only the first time a DWG is picked, which takes a few seconds; a DXF works too.
  - **Ground layers** (the surface) start as ELEVATION, FIELD <date> ELVS, CONTROL and ELEV_TREE. Tick others in or out; your choice is remembered on this computer.
    - **HIDE is always ignored:** those heights have already been dealt with.
    - Inverts are never treated as ground.
  - **What gets flagged:**
    - A ground shot more than **0.30 m** (adjustable) above or below **all** the points around it.
      - Ditch and bank shots (DB, BB …) are compared with their own kind nearby, so a ditch isn't flagged for being lower than the bank.
      - A FIELD-visit shot that disagrees with the original topo says "site change or error?".
    - **Trees** more than 0.30 m above (or below) the ground around them, e.g. a reflectorless trunk shot.
    - **Reflectorless shots not at target height 99**, on ground or tree points, when the package holds the raw shots.
    - The **same spot shot twice** at heights more than 0.10 m apart, and **0.00 elevations** on a ground layer.
  - **The view:** a plan of the points coloured by height, with contours (0.25 / 0.5 / 1 m or off) and flagged points circled. A bad height shows as a bullseye.
    - Scroll to zoom, drag to move, click a point to see its number, description, height, layer and why it's flagged.
    - Below the plan is the list (click a row to go to it) and **Copy list**.
  - The flags are *worth a look*, not verdicts: a real pit, mound or wall can stand out too.
  - Tested on 26-3582: it flags 5160, 5398, 5186, 4216 and 4199 (the bullseyes in your contours) and no trees. A height raised 1.2 m and a tree shot 1.5 m up the trunk were both caught.
- **PM › BC Assessment** button under each site address, alongside ParcelMap BC, Job map and Google Maps (the address is copied, ready to paste). BC Assessment is also added to Resources.
- **PM › Next quote number: no silent jumps.**
  - The note now names the folder the count started from ("Next free number after 26-652 ('Elev. Survey Quotes 26-652-…')").
  - If the next number would skip a run of unused numbers, it warns ("26-652 may be a mistyped number") and offers **Use 26-643 instead**. This covers a lone or mistyped folder, like the jump that turned 26-643 into 26-653.
  - A Quote # brought in from a tracker row that skips numbers is questioned the same way before its folder is created.
  - **Renumber…** works the same way.
- **PM › Convert to job: the job folder is found by its last digits.** Job numbers run in one sequence, so if the year part is typed wrong (24-2353), the app finds **23-2353**, asks, and uses it (fixing the Job # field). It never makes a second folder for the same job digits.
- **PM › Tidy moves folders file by file instead of copying them.**
  - The browser can move files but not folders, so a folder like DRAFTS or "Field Data 2021" is re-made in its new place and every file is moved into it, subfolders included. There are no duplicate copies to check.
  - The old folders are left **empty** and listed as "Now empty — safe to delete". The app still never deletes anything.

## Build 1.36 — 2026-10-27
- **PM › Scope page on the Word quote** (optional).
  - Under *Quote document*, **Scope page** adds a page in one of three ways:
    - **From a PDF…**: pick the PDF, then click the page to use (a multi-page PDF shows thumbnails).
    - **From a picture…**: a PNG or JPG.
    - Click the box and paste a screenshot (Ctrl+V), or drop a file on it.
  - Add a caption if you like (e.g. "Scope of work — highlighted area"). Usually there's one page; **+ another page** covers the rare case of several.
  - On the Word quote, it's its own page after the signature block and **before the rate sheet**: a teal **SCOPE OF WORK** heading, the picture at full page width (proportions kept), then the caption.
  - The quote points to it: "See page 2 for the scope of work and page 3 for our hourly rates, fees & deliverables." A note that mentions the attached hourly rate sheet now says "…on page 3".
    - These are Word page fields, so Word corrects them if the quote runs longer; they refresh when you print or save as PDF.
    - The numbers the app writes are its own estimate, checked against 30+ test quotes of different lengths.
  - The picture is kept with the draft on this computer, shown in the live preview, and saved inside the Word file. Reopening the Word quote with **Open a quote** brings the picture back, even on another computer.
  - Sub-quotes start without a scope page.
- **Fix — tracker rows pasted together could become "linked" drafts.**
  - Quotes made at the same moment (several rows pasted at once) got the same hidden ID, so selecting, saving or deleting one affected the other.
  - Every draft now gets its own ID, and drafts already linked are separated automatically when the app opens; both are kept.
- **Fix — tracker paste with two emails in one cell** ("a@x.com, b@y.ca"). A selection that doesn't start at column A now lines up correctly instead of shifting every field. Only a real quote number (e.g. 26-641) is ever put in Quote #.
- **PM › Job map preview:** once you click into the map to pan or zoom, the green pin hides (it marks the frame centre, so it would drift) and a note says so. **Re-centre** brings back the map at the address with the pin. Tip: the map's + / − buttons zoom on the centre.

## Build 1.35 — 2026-10-26
- **PM › Research buttons under each site address.**
  - **City GIS** is picked from the city in the address, using the same list as the Resources tab (Surrey → COSMOS, Coquitlam, Burnaby, Vancouver and so on).
    - "North Vancouver" or "Langley" on its own shows both the City and the District / Township, unless the address lookup settles which.
    - If no city is typed, the address lookup supplies it.
  - **ParcelMap BC** (maps.ltsa.ca), **Job map** (your Google My Maps, at the address) and **Google Maps**.
  - Most of these sites can't open straight to an address, so clicking a button copies the address first; ParcelMap BC copies the PID when there is one. Paste it into the site's search with Ctrl+V.
  - Each property on a quote gets its own buttons, and they follow the address as you type.
  - They aren't shown on sub-quotes (e.g. 26-616B), where the research was already done.
- **PM › Job map preview with the address pinned.**
  - When an address is entered, the app finds it on the BC Address Geocoder (the Province's free address lookup).
  - It then opens your job map right on the quote page, zoomed to that address, with a green pin on it.
  - It's your live job map, so new jobs you add show up; Google may take a few minutes to show the latest changes.
  - Click any marker for that job's details. Pan and zoom as usual. **Re-centre** goes back to the address, and **Open in My Maps** opens the full map there.
  - The green pin only marks the quote's address and is never added to your map.
  - If the address is only an approximate match, there's no pin and the app says so. **Hide job map** / **Job map preview** turns it off and on, and the app remembers your choice.
  - Not shown on sub-quotes.
- **PM › A shorter quote row.**
  - The row shows the **5 most recently edited** quotes, plus the one that's open and **every NOT SAVED quote**. **Show all** lists the rest.
  - **Clear completed quotes** removes quotes that are saved and unchanged since from this computer. It asks first, listing them, and never touches NOT SAVED quotes or the open one. Their Word quote and job details stay in the quote folders; reopen any with **Open a quote**.
- **Resources:** ParcelMap BC (LTSA) added to Provincial / federal.

## Build 1.34 — 2026-10-22
- **PM › Live quote preview.** The quote as it will print sits beside the services and updates as you type, tick lines, change prices or move services.
  - It shows the To: line, Quote #, date, the teal site address bar, numbered services with their lettered lines, prices, red lines, GST, disbursements and the signatory.
  - It's built from the same data as the Word quote, so the two always match. Page breaks and fonts may differ slightly. **Download quote (.docx)** still makes the real file.
  - **Show preview** (next to the Services heading) turns it off; the app remembers your choice. On narrower screens the preview sits below the services.
- **PM › Options shown as they print.**
  - A service set to *Option (choose one)* shows a bold **Option 1:**, **Option 2:**… before its title. The numbers follow the card order, the same as the Word quote.
  - An *Optional add-on* shows **(Optional)** after its title.
  - If only one service is set to Option, the card reminds you to add another option or set it to Included / Optional add-on. It's only a reminder.
- **PM › Red lines.** The red **A** beside any scope line or note prints that line in red on the Word quote (e.g. "Includes all services in option #1"). The letter stays black. Click again for black. Red lines are kept in saved versions, quote sets and when the Word quote is reopened.
- **PM › Hours presets** (each PM's own, on their computer).
  - **Save hours as preset…** on a service saves its hours under a name you choose ("Basic topo hours", "New construction hours"). With stages, each stage's name and hours are saved too.
  - **Hours preset ▾** on any service loads one. It replaces that service's hours and stages, and asks first if there are hours already. The list shows what's inside each preset, e.g. "3 stages · 6.0 field · 4.5 office".
  - Only hours are saved, never dollar amounts, so prices always come from the current rates. A role that's no longer in the rates is skipped, and the app says which.
  - Rename or delete them under **My hours presets**.
- **PM › Quote sets** (each PM's own).
  - **Save these services as a set…** (beside + Add service) saves every service on the quote together: wording, ticked and red lines, notes, and Included / Optional / Option.
  - You choose whether to include the hours (hours only, never prices). Client, site, prices and disbursements are never saved.
  - Load a set from the first dropdown on any service → **My quote sets**. All its services are added there, filling the empty service first.
  - Rename or delete them under **My quote sets**.
  - Export / Import (under My saved versions) now moves your saved versions, hours presets and quote sets together. Older export files still import.
- **PM › One wording picker.**
  - The second dropdown on each service is gone. The first dropdown loads the approved wording for a job type, or one of your saved versions (★).
  - A card using your version shows **★ My version: …**, with a button to go back to the approved wording.
- **PM › Strata package in the dropdown.** The "+ Strata package" button is gone. Pick **Strata package (townhouse / condo / mixed) — adds 4 services** in the Strata group of the first dropdown to add all four at once. The four pieces aren't offered one at a time any more.
- **PM › Final strata plan: Form V ticked by default.** "Signed Form V of unit entitlement areas" is a standard line now, since the surveyor prepares it for almost every strata plan. Untick it in the rare case it isn't needed. (Library change, in the new pm-vault.json.)
- **PM › Job details: options named and totalled.**
  - Options read "Option 1 — Building Location Certificate: 4.0 hrs 2 MAN CREW", and optional add-ons read "Posting plan (Optional add-on)", instead of "(option — not in total)".
  - With options on the quote, each one gets its own line: "Option 1 total before GST: $1,270.00 ($1,225.00 labour + $45.00 disbursements)". When there are also included services, they're added in.
  - When every service is an option, the $0 labour and disbursements-only total lines are left out. The same totals show on screen.
  - Older job details files still open.
- **PM › Save both to quote folder (Word quote + job details)** is the new name of the Save to quote folder button. Copy job details and Copy tracker row have hover tips saying what each is for.
- **Fix — reopening a Word quote that was edited and saved in Word** (e.g. 26-632).
  - Word sometimes renames the hidden style names the app uses to find each service (EQService became EQServiceTitle, and so on). The app then found no services and offered "3 service(s) removed in Word". Clicking OK left the quote with no services.
  - The app now reads both names, so your Word edits come back with the services, and the hours stay from the app.
  - If the services in a Word file still can't be read, the app never empties the quote. It opens its own saved version and says so.
- **PM › Rate sheet (page 2) formatting** matches the office sheet: rates and fees in bold, and the $400 minimum charge line in red.

## Build 1.33 — 2026-10-21
- **PM › Save to quote folder: dates in file names are no longer read as quote numbers.**
  - Only files with "quote" in the name are checked for a quote number. Example: in 26-623-Astria Properties, "2026-10-20 Survey Extents.pdf" was read as quote "10-20" and you were asked which folder to use.
  - A quote file naming another quote (e.g. a copied 26-174 quote) still asks.
- **PM › Duplicate as sub-quote also clears four more fields:** Services Provided, Additional Task Details, Additional PM comments and Date requested.
- **PM › saved versions are easier to use.**
  - **My saved versions** has a **Use** button beside each version. It fills the empty service on the open quote, or adds a new service if they're all in use.
  - Every service card's first (job-type) dropdown has a **My saved versions** group (★). Pick one to apply that version to that service.

## Build 1.32 — 2026-10-20
- **PM › Duplicate as sub-quote copies only the job details.** A sub-quote is new services and new hours; changes to the original go on the original quote.
  - Kept: the top section (client, contact, email, phone, site address(es) incl. extra properties, project line, legal, PID, plans, PM name / initials) under the new sub-quote number.
  - Blank, as on a new quote:
    - services (one empty service), hours, stages and price lines;
    - every typed or held price, including "Hourly" and per-unit prices;
    - disbursements, Field Crew Instructions, notes and the rate-sheet option.
  - A note on the sub-quote says so. The original quote is untouched.
- **PM › Renumber… a quote.** For when another quote already has the same number.
  - The **Renumber…** button sits above the Quote #. It's also offered in the "More than one folder could be quote … — which one?" box.
  - It suggests the next free number this year (checks the Quotes - Documents folders and your drafts) and refuses a number already used by a folder or a draft.
  - On confirm it updates the Quote # and Word file name. Then create this quote's folder with "Create quote folder", and update the To Do Quotes tracker.
  - The other quote and its folder are never touched, and nothing is created automatically.
- **PM › reminder when no disbursements are selected.** "No disbursements selected — title, plans, checklist or filing fee?" shows under the Save / Download buttons.
  - It's only a reminder: saving and downloading still work.
  - It disappears as soon as a disbursement or an "other" amount is entered.
- **Fix — Match points (General and Calc → tied-in) since 1.31.**
  - The 1.31 Monitoring code reused a name the matcher relies on. This broke the monument-ID check: every pair showed ✓ID, even G or CHK shots, and the ID hints that steer the match were scrambled.
  - Fixed. IDs are read correctly again (2022 "ocnt 6292" = 146 OCNT 6292).
  - New: a crew note naming the other side's point number with its code ("105 occ" → 105 OCC, "opcon 111" → 111 OPCON) also counts as a hint.
  - With two or more hints, a match that pairs none of them (e.g. a chance triangle of ground shots) is no longer accepted. The tool loosens the tolerance for one that agrees with the hints.
  - Where a hinted point and a backsight check sit on the same spot, the hinted point is named.
  - A scale difference between the sides (e.g. UTM grid vs local ground) is now reported. It is never applied; the Helmert in MS CAD solves it.
  - Checked on 23-2362 lease: 2022 → 146, 2023 → 111 and 2024 → 105, the same pairs as the MS CAD Helmert (scale ≈ 1.0004). Before the fix it gave 2006 → 147, 2002 → 109, 2005 → 143.
- Verified with a test vault: the sub-quote keeps the job details (incl. a 2nd property) and clears services, held prices, price lines, disbursements, crew instructions, notes and rate sheet, with the original unchanged. Renumber was checked with drafts only (suggests the next after the drafts) and with folders (two 26-618 folders and a 26-652: suggests 26-653, refuses 26-652 and a draft's number, creates and touches no folder), and from the "more than one folder" box. The reminder shows, hides and doesn't block. All earlier checks still pass.

## Build 1.31 — 2026-10-19
- **Points tab: tool buttons.** The tools are buttons along the top: Clean-up · Scale · Match points · Design vs Field · Monitoring · Tree table · Transform.
  - One tool shows at a time, so there's no scrolling past the others. The file shelf stays at the top for every tool.
  - Clean-up opens first, and the app remembers the last tool you used. Tree table is greyed out when the file has no trees.
- **Training videos in the Points tab.** Each tool shows its own ▶ Training links, which open the video in a new tab:
  - Clean-up: tree sizes to imperial, points upload for crew, RW5 to points in feet;
  - Match points: points matching, plus the PL sample;
  - Design vs Field: cut / fills, and residuals;
  - Tree table: tree table.
- **Points tab: Monitoring** (new). Compares the base (true) values with this trip (observed). The residual is **observed − base**, to the mm. Residuals only, no tolerances applied, and nothing is saved between sessions.
  - **Base:** paste it from the monitoring spreadsheet (copy the header + values), or pick its point range from a file.
    - The pasted header decides the layout: "Elevation" only, or N / E / Ele. "Gauge" / "Guage" labels are fine.
  - **This trip:** type the trip's point range; only those shots are used. A suggested range (the newest shots on the base points) can be accepted with one click.
  - **Pairing:**
    - Shots are paired to the base points by position (default within 0.10 m).
    - Repeat shots of a point within the trip are averaged, with the shot count and spread shown.
    - With an elevation-only paste, shots are matched by their description (A, B, …) inside the trip range. A point coded twice far apart is flagged and not averaged. Picking the base by range instead pairs by position.
  - **Copy for the spreadsheet:** rows in the base's order with its labels: observed values (optional), then ΔN ΔE ΔEle (+ ΔTotal), or Elevation only.
  - Averages and base values are rounded to the mm before differencing, as in the spreadsheets.
- **Design vs Field:**
  - **Point ranges** box for each side (e.g. "625-663, 700-750, 812"). It's used instead of the blocks when filled in, for jobs with several days of shots.
  - The **Note** column lists other field shots also inside the search limit ("also within 0.30 m: 898"). It never chooses between them.
  - With only **Cut / fill** ticked, points without a design elevation are left out of the .dxf table and Copy table. The on-screen table still shows every row.
- **Tree table:** has its own Metric / Imperial switch (the same setting as Clean-up).
- **Training tab:** added RW5 file to points for a topo in feet; Design vs Field cut / fills and residuals; Tree table; a new LISP commands section (cert in metres to feet, feet to metric topo example); Creating blocks; Dimensioning in feet and inches.
- Verified:
  - Monitoring on 22-1740 (Oct 7 trip against the Oct 6 baseline, pasted from the spreadsheet): all 9 points paired, F and I averaged, ΔN / ΔE / ΔEle / ΔTotal matching the report (as observed − base).
  - Monitoring on 24-2709 (May-1 base pasted as Elevation only): matches the PDF's 2nd, 3rd and 4th readings exactly. The 2nd needed the base picked by range, because shot 746 is coded "C" but sits on D; with an elevation-only paste it is flagged, not averaged.
  - Design vs Field ranges, notes and Cut / fill-only rows, plus the tool buttons and training links, checked on 24-2817. All earlier checks still pass.

## Build 1.30 — 2026-10-15
Includes everything from 1.29, which was only live for a few hours, plus the first round of feedback on it.

- **Points tab: Design vs Field** (panel under Match points). Compares design points with the field shots for stake-outs, cut / fill and as-builts. Load one .msz holding both, or a field .rw5 / points file next to a design .msz on the shelf.
  - **Pairing.** Each design point is paired with the nearest field point. Tap point-number blocks to choose the Design and Field sets; with one file, points numbered under 100 start as Design and everything else as Field. Pick the stake-out shots for Field, so pins or ground shots at the same spot aren't used.
  - **Search limit (default 0.30 m).** Design points with no field point that close are left out of the results. The summary line just counts them.
  - **Residuals only, no pass / fail.** There is no MEET, no ON and no tolerance check; you judge what's acceptable for the site.
    - ΔN / ΔE are field minus design, to the mm, shown as where the stake sits ("0.121S 0.004W").
    - Cut / fill is design elevation minus field elevation, both rounded to the cm (the office method): FILL when the ground is below design, CUT when it's above, CUT0.00 when exactly on grade.
    - A design elevation of 0 means horizontal only.
  - **On-screen table.** Every column, plus the field description and a note when one field point is nearest to two design points: Design pt, Field pt, Design elev, Field elev, Cut/Fill, ΔN, ΔE, Horiz.
  - **Include switches.** Horizontal ΔN / ΔE, Cut / fill, and Horizontal distance (off by default). They decide what goes into the stakes' descriptions and which columns go into the .dxf and Copy table. Point numbers are always in. The elevation columns drop on their own when none of the design points has an elevation.
  - **Table for the drawing (.dxf).** Lines and text on layer ELV-DESIGN-FIELD, with a text height you set, to insert as a block beside the plan. Copy table pastes into Excel as columns.
  - **Points file with amended descriptions (.txt).** The field file with only the paired stakes' descriptions changed, e.g. "FILL0.34 0.121S 0.004W". An existing description is kept ("G FILL0.90 …"), and numbers and coordinates are untouched. Import it into MicroSurvey over the existing points so the results show on the drawing. "Changed points only" gives just the amended stakes. Both always save as .txt, whatever the source file was.
- **Points tab: Tree table** (panel under Design vs Field; shows when the file has trees). Every tree point (TCED, TCLU, TCLUS, TCON, TDEC, TFIR, TSTUMP) by point number, in numeric order.
  - The description is worded as the AutoMap writes it, built from the cleaned descriptions: metric "30cmØ deciduous Dr=4", or imperial (following the drawing units) "0.98Ø deciduous Dr=13.12". There is never "cm" on an imperial drawing, including TCLU.
  - Tree table for the drawing (.dxf) has PT and DESCRIPTION columns on layer ELV-TREE-TABLE. Long lists wrap into side-by-side column sets; rows per set default 40, adjustable. Copy list is also available.
  - On the drawing, show the point numbers beside the tree symbols (e.g. a tree point-number layer) so the table can be cross-referenced.
- **Jobs: Tidy this job folder**, fixed for older job folders like 21-1323:
  - Capitals don't matter ("request", "REQUESTS", "office", "FIELD").
  - Any folder named with "request", "field data" / "field notes" or "data" is recognised, including ones already inside Office or Field. Approval folders go into Office › Requests.
  - When there's no Requests or Data folder yet, the old folder becomes it, instead of a new empty one being made beside it. When there is one, the old folder's contents go into it, and files already there are kept, never replaced.
  - If the browser can't move a folder (Edge / Chrome often can't move folders with subfolders), it is copied instead, subfolders and all, and checked. The original is listed for you to delete; the app still never deletes anything.
- Verified: Design vs Field on 24-2817 against the office's hand-calculated cut / fill plan. 35 of 36 agree; the one difference, point 76, is a sign slip on the plan (ground 41.55, design 41.47 = CUT0.08, plan shows FILL0.08). Also checked: horizontal-only calc corners, design points with no stake left out, the column switches, the .txt names, the amended points file (only descriptions change), and both .dxf tables (opened in a CAD reader). The tree table was checked metric and imperial, with units typed into descriptions and cm drip lines. Tidy was tested with folder moves blocked and with lower-case Office / Field folders. All earlier checks still pass.

## Build 1.29 — 2026-10-15
- First release of Design vs Field and the Tidy fix; live for a few hours and superseded by 1.30, which describes everything.

## Build 1.28 — 2026-10-13
- **Quotes: Legal Plan to close Road** (Posting & reference plans), from 20-155-D: "To cover area for Road closure By-law", plus all legal property pins set on site, digital UTM file, legal plan prepared + certified, and the plan to be filed by the client's lawyer. Choosing it adds 1 checklist fee to the disbursements.
- **Quotes: strata package for townhouse / condo / mixed projects**, from 20-155-E and kept separate from the Duplex–Townhouse final strata plan. "+ Strata package" under the services adds four one-line services (preliminary strata plan for the disclosure statement; excavation, building layout and forms certificate; posting plan before the final strata plan; final strata plan from field measurements). Remove any you don't need with ✕. Prices start blank. The last service carries the closing note "Any additional work or significant revisions to be billed at hourly rates (Field – $220/hr; Office – $125/hr; BCLS – $190/hr)", filled in from the current rates, or pointing to the attached rate sheet when that's ticked.
- **Price per unit or per building** (any service). Next to the price, choose Flat price / Per unit / Per building, then type the number and the price each. The Word quote shows "$90 per unit (total $1,800)". The total counts in the job total, and the job details show "Quoted price: $1,800.00 (20 units × $90)".
- **Project line** (optional) under the site address, e.g. "5 BUILDING (TWENTY UNITS) TOWNHOUSE COMPLEX". It prints on the line below the address in the same bar of the Word quote.
- **Points tab: tree sizes typed with units** ("TDEC 5CM 50", "TFIR 30 CM 2M", "TSTUMP 40cm") are now fixed automatically: the units are dropped (diameter in cm, drip line in m), so the drip-line and imperial conversions pick them up too ("TDEC 5CM 50" → "TDEC 5 0.5", or "TDEC 0.16 1.64" for an imperial drawing).
- **Job details: hours with stages and several services.** Estimated Field / Draft Time now give the total per role on the top line, and each service on its own line below, with a staged service showing its stages in brackets ("New House Construction: 8.0 hrs 2 MAN CREW (4.0 excavation layout + 2.0 foundation layout + 2.0 forms certificate)"). Before, the other service's hours sat unlabelled at the start of the stage list. A single staged service still lists its stages on the top line as in 1.26.
- **Quarter hours are no longer rounded** in the job details: 0.75 hrs prints as 0.75 (was 0.8), so hours × rate always matches the amount beside it ($93.75).
- **Checklists: feet or metres.** Topographic: a tree sizes / drip lines item at the end of General topo requirements (converted to feet for an imperial topo), and an imperial-tree check at the end of Project Manager Checks. New Construction: at the certificate stage only (end of General certificate requirements), check if the certificate needs to be in feet or metres, checking the existing topo drawing (typically feet in Burnaby, Vancouver, North Van and New Westminster). Added at the end of each section, so checklists already in progress keep their ticks.
- Library changes (road closure + four strata-package services) are in the new pm-vault.json; rates, disbursements, crew instructions and the rate sheet are unchanged.
- Verified: road closure, strata package, per-unit / per-building prices, the project line and the rate-sheet wording in the Word quote and job details; job details hours with stages; tree sizes with units; all earlier checks still pass.

## Build 1.27 — 2026-10-09
- Internal update; no changes to the shared tabs.

## Build 1.26 — 2026-10-08
- **Stages within a service.** "+ Add stage" splits a service into stages / trips (e.g. Legal + excavation layout, Building layout, Forms certificate), each with its own field and office hours. All stages add up to the service's one price and count in the job total; the Word quote still shows one service and one price. Job details: Estimated Field Time lists each stage ("4.0 hrs 1 MAN CREW (legal + excavation layout) + …"), Estimated Draft Time gives each role with the stages in brackets ("3.0 hrs CAD TECH (1.5 legal + excavation layout + 0.5 building layout + 1.0 forms certificate)"), and the Sublabour Calculation has a block per stage. Adding the first stage keeps the hours already entered as stage 1. Price lines (future trips) still work alongside. The job details file and the Word quote reopen with the stages.
- New House Construction (both) and New Construction now open with their stages already named from the scope lines, hours blank — rename, reorder, remove or add per quote.
- **Name by client or contact.** Create quote folder now uses the client (anything in brackets dropped, e.g. "Manjit Kaila (Developer)" → "26-604-Manjit Kaila"); when the quote has both a client and a different contact, "Name by: Client / Contact" lets you switch. The Word file name follows the same choice.
- **Your name stays the Project Manager.** Opening a job details file or Word quote from another PM, or making a sub-quote, keeps your Project Manager name and initials; the import note shows what the file had ("In the file: Project Manager TC — kept yours").
- **Numbered sub-quotes.** 24-165-1, 24-165-2 (and 24-165 2) are recognised like 26-586B: the Quote # finds the 24-165 folder, saves into it, converts to a job and picks its own job details file. Duplicate as sub-quote follows the folder's style — 24-165-3 after -1 and -2, D after B and C, B when there are none.
- **Duplicate as sub-quote with only the Quote # typed** now fills the details from the quote folder first (the app's Word quote for that number, else its job details file) and says where they came from; the empty draft is replaced.
- **Jobs: drop a file.** Dropping a Word quote or job details file on the Jobs view fills the Quote #, finds the quote folder and fills client and site (it no longer opens a draft under Quotes). With sub-quotes in the folder, the Word quote / job details file matching the Quote # is used.
- **Add to existing job.** If the job folder already exists (a sub-call), the button becomes Add to existing job: it copies the quote's files into Office (files already there are kept), adds Office › Requests › yy-mm-dd-approval and any missing Field / Office folders. The renamed job details goes in as "24-2636-job details (24-165-1).txt" when the job already has one.
- **Tidy this job folder.** Entering a job number whose folder isn't in the usual layout shows what Tidy would do: create Field › Data, Uploads and Office › Obsolete, Requests, move the contents of "Field data" into Field › Data, the contents of "requests" into Office › Requests, and everything else into Office. You confirm first; whatever the browser can't move is listed to drag in File Explorer; nothing is deleted or overwritten (emptied folders are left for you to delete).
- Save to quote folder: clearer message when no folder is found (choose it, or create it with Create quote folder).
- Verified: 26-435-style new construction (3 stages, $1,935) in the job details, Word quote and reopen; 24-165 → 24-165-3 from Quote-24-165-job details.txt; 24-2636 tidy with and without browser move support, and Add to existing job; all earlier checks still pass.

## Build 1.25 — 2026-10-07
- **RW5 raw data → points file (Points tab).** Drop a .rw5 from the data collector on the Points tab. The app reads it (the file is never changed), lists the stored points, the measured shots and each setup, and works out coordinates for the measured shots from the setup, backsight, instrument and target heights (each target-height change, reflectorless shots, scale factor, EDM offset and curvature/refraction when the file has them on). Check shots to points already in the file, such as the backsight check, are listed with their differences and never overwrite the stored coordinates. Choose Everything (one file), Measured shots only, Stored points only, or Two separate files — each downloads as comma-separated P,N,E,Z,D and goes on the shelf for cleanup or Match points. GPS points written with grid coordinates (--GS lines) are read as stored points; a shot that can't be reduced (no setup, backsight or distance) is listed, never guessed.
- **Duplicate as sub-quote checks the quote folder.** The next letter now comes from the files already in the quote's folder (26-586B, 26-586-C, 26-586 C in Word quote and job details names) as well as the drafts on this computer, and the note says what it found ("26-586B, 26-586C already there — this is 26-586D"). With folders not connected it uses the drafts, and says so.
- **Paste a list into the scope.** Copy the list of items from a client's email and paste it into any scope line (or note) on a service: each line becomes its own scope line, in order, right after the one you pasted into (an empty line is used for the first item). Bullets, dashes and numbering (1. a) •) and full stops at the end are dropped; blank lines are skipped.
- Save to quote folder: if a new sub-quote's files are already in the folder, it offers to save it as the next free letter instead of only replace or keep.
- **Disbursements start at $0 on a new quote** (previously 1 title + 1 legal plan = $45 was pre-filled). Add what each job needs.
- Opening a job details file made outside the app: a Disbursements line that is only a total ("Disbursements: $45") is no longer put under Other (it was being counted again on top of the title/plan counts); the import note asks for the counts instead. Lists such as "1 title, 2 legal plans" or "$45 (1 title, 2 legal plans)" are read into the counts. Estimated Field Time in days ("1.5 days (2man)") is read as 8-hour days (12 hrs 2-man crew).
- **Quote folder tidy-up always creates the range folder.** When the tidy-up is ticked, "Elev. Survey Quotes 26-500-26-599" (or "2026 Quotes" at a new year) is created even when the browser can't move folders; the message then lists exactly which folders to drag into it in File Explorer. Nothing is ever deleted or overwritten.
- Verified: 26-3647F06OCT26.rw5 — 552 stored points and 102 measured shots; backsight checks to 100 and 346 come out within 3 mm horizontally and 1.5 cm in elevation, matching the deltas the data collector recorded; 707 "P CEN" lands on the centre of design points 500–503. Sub-quote letters and the save offer tested against a stand-in quote folder; all earlier checks still pass.

## Build 1.24.1 — 2026-10-06
- Training tab: Elevate Office app — PM tab now also has "Sub-quote for an existing quote folder".
- Everything from 1.24 is included, so this build can be uploaded on its own.

## Build 1.24 — 2026-10-06
- **Several prices for one service.** "+ Add price line" on a service card adds a second price for the same service (e.g. 1st trip to setup / Any future trips), each with its own label (pick-list or free text), its own field and office hours, and its own calculated or typed price. The Word quote shows one service with the prices stacked in the price column, each with its label underneath; nothing is marked Optional or Additional.
- Job details keep each price line's hours separate under the same service ("Price line 1 — 1st trip to setup", "Price line 2 — Any future trips (per trip, not in total)"). Totals count price line 1 only; Estimated Field/Draft Time list each line under the service. The .txt and the Word quote both reopen with all price lines.
- **Price note.** Each service has an optional Price note that prints as *note under the service and puts * in front of the price (e.g. *$3,380). "Rate-sheet wording" fills in the 3-trip wording that points to the attached rate sheet and ticks the rate sheet.
- **Attach rate sheet (page 2).** A tick under Quote document adds a second page: the letterhead, a "RATES, FEES, & DELIVERABLES FOR 2026" bar, then Rates, Additional Fees/Disbursements and Deliverables with the footnotes. Rates and fees come from the current rates in the vault, so the sheet follows any rate change; the year updates itself. No boxes or ruled lines on the page (Acrobat's Prepare Form turns those into form fields). The quote can't be built if a price note mentions the rate sheet but the tick is off.
- pm-vault.json: rate-sheet wording added (legal plan scan copy $70, drone minimums, deliverables, footnotes). Rates, library and crew instructions unchanged.
- Tools: Feet-inches ↔ metres — type a metric value with an m (3.81 m) to see it as feet-inches (12' 6", to the nearest 1/8"; ≈ when rounded) and decimal feet. Anything without an m works as before.
- Training tab: Elevate Office app — fixing tree sizes to imperial; new Elevate Office app — PM tab group: cert quote on the PM tab, convert a quote to a job, setting up the connection to the Quotes + Jobs folders, topo + posting option.
- Verified: monitoring quote (26-595 layout) and new construction quote with rate sheet (26-596 layout) built, rendered and reopened from Word and from the job details file; page 2 has no lines or boxes apart from the teal heading bar (same as the site address bar); all earlier checks still pass.

## Build 1.23.1 — 2026-10-05
- **Tracker rows for the same client become one quote with several properties.** When the rows you paste from To Do Quotes have the same client (or contact) and email but different site addresses, the app asks: OK = one quote with each address as its own property (Site Address, PID, Legal Desc. per property, "SITE ADDRESSES:" on the Word quote); Cancel = a separate quote for each site, as before. Services, notes and dates from the rows are combined without repeats.
- Pasting a selection that doesn't start at column A (e.g. Client to Service) now lines the cells up by the email column, instead of putting the client name in Quote #.
- The What's new card now reads its notes from this build's CHANGELOG.md entry, so it always matches the build (it had been showing older Points notes).
- Verified: the Inderjit Singh rows (10142 128A Street and 9088 126th Street) join into one quote with two properties or stay separate on Cancel; partial and wide selections; all earlier checks still pass.

## Build 1.23 — 2026-10-02
- **Older quote folders are found too.** Find quote folder, Save to quote folder, Jobs and the next-number check now understand every naming used since 2020: "Elev. Survey Quote 21-015-…" (Quote without the s), "Elev.Survey Quotes 23-755-…" (no space), and range folders written "21-100-199", "21-01-099", "23-001-099" as well as "26-400-26-499". Checked against the real Quotes - Documents: quotes from every year 2020–2026 are found (e.g. 21-015 in 2021 Quotes › 21-01-099), and the next number is still 26-593.
- **Sub-quotes however they're written.** 26-568C, 26-568-C and 26-568 C all belong to the 26-568 folder: Find quote folder and Jobs open it, the Quotes view shows "Quote folder: …26-568-…" instead of offering a new folder, and a sub-quote without a folder offers the main quote's number (the Quote # stays 26-568-C).
- **Job details renamed reliably when converting to a job.** Any job details text file is recognised (quote-26-568-C-job_details.txt, Quote-26-233-job details.txt, …). If the quote folder holds several (26-568, 26-568B, 26-568-C), only the one for the quote being converted becomes "26-3646-job details.txt"; the others are copied with their names unchanged. The preview shows which one.
- **Create quote folder** moved to the top of the quote, above the fields; its "needs the client or contact name" hint now disappears as soon as a name is typed.
- **City map links updated:** West Vancouver (new maps page), City of Langley (maps.langleycity.ca — the old link had a typo), Mission (map.mission.ca), Pitt Meadows (MapView), Port Coquitlam (opens PoCoMap directly), Vancouver (new VanMap at geoportal.vancouver.ca), Delta (maps.delta.ca), North Vancouver City (secure https).
- Field Crew Instructions Option 4 (Vancouver/Burnaby) now asks for the basic building outline of the existing house — in the pm-vault.json sent earlier today.
- Verified: older names, sub-quote variants, job details choice, button position and hint, links; all earlier checks still pass.

## Build 1.22.2 — 2026-10-01
- **Word quotes are now packed the way Word packs them.** The app wrote its .docx files uncompressed with placeholder 1980 dates. They open fine in Word, but when one lands in a SharePoint library, Office's upload (which merges the library's properties into the file) failed on it — Word showed "UPLOAD BLOCKED", OneDrive sat on "Sync pending", and Acrobat's Create PDF couldn't open it. A copy re-saved by Word/SharePoint of the very same quote synced and converted at once. Every part is now compressed like Word's own files (about 40% smaller) and stamped with the real time. Reopening quotes made by earlier builds still works.
- Verified: Word files pass validation, reopen with their draft, 26-590 still fits on one page; all earlier checks still pass.

## Build 1.22.1 — 2026-10-01
- **Word quotes no longer carry another library's SharePoint settings.** The 2023 letterhead file the template was built from still held hidden SharePoint document-library information from the library it was originally saved in (its content type and managed-metadata fields). Every quote inherited it. When such a file lands in Quotes - Documents, Office has to reconcile those settings during OneDrive's upload, which is the likely reason today's Word quotes sat on "syncing". The template now has none of it — the quote looks and prints exactly the same, and the app's own draft inside the Word file (for reopening) is kept. **Upload the new quote-master.docx** with this build.
- Verified: Word files pass validation, reopen with their draft, 26-590 still fits one page; all earlier checks still pass.

## Build 1.22 — 2026-10-01
- **Quote folders follow your Quotes - Documents layout** — the current hundred loose at the top, finished hundreds in range folders ("Elev. Survey Quotes 26-400-26-499"), past years in "2025 Quotes" (its ranges plus that year's last hundred loose):
  - **Next quote number** now counts the quotes inside the range and year folders too, so it stays right after a hundred has been tidied away (before, it only looked at the top level). The 26-000 template folder and the range folders' own names are never mistaken for quotes. Numbers are three digits (27-001).
  - **Find quote folder, Save to quote folder and Jobs** now look inside the matching range folder and year folder, so older quotes such as 26-450 or 25-747 are found automatically.
- **Tidy-up offered automatically, the usual way.** When the next quote folder starts a new hundred (26-600), the confirmation also offers — ticked — to move 26-500 … 26-599 into a new "Elev. Survey Quotes 26-500-26-599". At the first quote of a new year (27-001), it offers to move all of last year's folders into "2026 Quotes", leaving that year's last hundred loose inside, as in 2025 Quotes. The folders being moved are listed; untick to skip. This is the only time the app moves anything, and only on your Create folder. If the browser can't move folders, the quote folder is still created and the app lists exactly which folders to drag where.
- Verified on a copy of the real layout: 26-450 and 26-499 found inside 26-400-26-499 (not confused with the range folder), 25-747 inside 2025 Quotes, next number 26-600, tidy of 100 folders, next 26-601 after the tidy, untick leaves things alone, no-move browser fallback, new-year 27-001 with 2026 Quotes; all earlier checks still pass.

## Build 1.21 — 2026-10-01
- **Create the next quote folder from the PM tab** (Quotes side, under the fields; needs *Quotes - Documents* connected under Folders on this computer). **Create next quote folder** looks through Quotes - Documents for the highest number this year (e.g. 26-590), proposes the next one — "Elev. Survey Quotes 26-591-Simon", named after the contact's first name or, with no contact, the client — and lets you change the name. Nothing is created until you press **Create folder**. Right before creating, it checks again; if another PM has just taken the number it uses the next free one and tells you. The quote's Quote # is set to the new number, with a reminder to add it to To Do Quotes.
- If the Quote # is already typed, the button reads "Create quote folder for 26-xxx": it uses an existing folder for that number if there is one, otherwise creates that exact number.
- Always optional: quotes from a tracker row (or typed in) are never given a folder automatically — the message after pasting a row points to the button for the ones that need one. The client or contact name must be filled in first.
- Verified: next-number logic (ignores last year's and non-quote folders), name choice and editing, number taken mid-way, existing folder reused, typed number, tracker-row quote with and without a folder, Save to quote folder finding the new folder; all earlier checks still pass.

## Build 1.20 — 2026-10-01
- **New quote from a To Do Quotes row.** In the tracker, select the whole row (click the row number), press Ctrl+C, then press Ctrl+V anywhere on the PM tab (Quotes side) — or use **New from tracker row** and paste into the box. A new quote opens with Quote #, Client, Contact, Email, Phone, Site Address, Services, Additional Task Details, Date requested, Assigned and PM comments filled in from columns A–K. Several rows make several quotes; the header row is skipped; cells with line breaks come through intact. If a draft with the same Quote # already exists it asks whether to fill that draft's empty fields or make a separate one. Pasting into a field still pastes normally.
- Verified: single and multiple rows, header row, multi-line and quoted cells, same-Quote # fill, paste box, job details carry the row; all earlier checks still pass.

## Build 1.19.2 — 2026-10-01
- **More room on page 1 of the Word quote.** Word was still moving the contract to page 2 on 26-590, so about 3/4 inch more space is freed on every quote: a little less space under the date and the Site Address bar and above each service, body line spacing 1.05 instead of 1.1, and an empty line at the bottom of the letterhead footer removed (the teal footer bar is lowered by the same amount, so the footer looks the same). Wording and font sizes are unchanged; the contract and signature lines still stay together. **Upload the new quote-master.docx** with this build.
- Verified: 26-590 rebuilt from its Word file fits on one page with room to spare; Word files pass validation; all earlier checks still pass.

## Build 1.19.1 — 2026-09-30
- **Word quote addressed to the client only:** "To: Schedio Spaces" instead of "To: Schedio Spaces - Simon Boisvert". The contact is used only when there is no client name, and it stays in the job details file as before.
- **Optional add-ons say so on the quote:** an Optional add-on's title now ends "(Optional)", e.g. "Posting plan for Permit Purposes (Optional)", beside its "Additional $1,330" price (not added twice if the title already says optional). Reopening the Word quote reads it back without doubling it.
- **Two services fit on one page more often:** GST EXTRA, the disbursements line and the signatory now follow straight after the last service; only the contract paragraph and the signature lines are kept together, so they still never split across pages. Spacing above each service and around the closing block is a little tighter; wording and font sizes are unchanged. When a quote doesn't fit, the contract and signature lines move to page 2 together. **Upload the new quote-master.docx** with this build.
- Verified: 26-590 rebuilt from the draft inside its Word file now fits on one page; a four-service quote still breaks cleanly between services; Word files pass validation; all earlier checks still pass.

## Build 1.19 — 2026-09-30
- **PM tab now has two parts: Quotes and Jobs** (switch at the top).
- **Folders on this computer** (bottom of the PM tab, Edge or Chrome): each PM connects their OneDrive-synced *Job Files - Documents* and *Quotes - Documents* once; OneDrive uploads whatever the app saves. The app only ever creates folders and adds files. It never deletes or moves anything, never creates a quote folder and never changes an existing job folder.
- **Save to quote folder** (Quotes, next to Download quote): saves the Word quote and the job details file straight into the quote's existing folder, found by its Quote # (26-561 never picks up 26-5610; if more than one folder could match, you choose). If either file is already there it asks before replacing it. If no folder matches, it says so, lets you choose the folder yourself, and creates nothing.
- **Jobs — convert an accepted quote to a job:**
  1. Enter the Quote # and **Find quote folder**, or press **Convert to job…** on the quote. The client and address are shown (from the draft on this computer or, if it has been tidied away, from the Word quote or job details file in the folder) so you can check it's the right quote. A folder whose number matches but whose files name a different quote (older folders were numbered separately) is never picked automatically — you choose, or pick any folder yourself.
  2. Enter the job number issued by the online app (the job record is entered there first, as now).
  3. **Create job folder** makes Job Files - Documents › 3000-3999 › 3400-3499 › 26-3466 with Field › Data, Uploads and Office › Obsolete, Requests › 26-09-30-approval (approval date editable), and copies everything from the quote folder into Office, renaming the job details file to "26-3466-job details.txt". A new hundreds range folder (e.g. 3500-3599) is created when needed. It stops without creating anything if the job folder already exists or the thousands folder isn't there.
- Verified against a stand-in of the folders: save/replace/keep in the quote folder, lookalike folders untouched, details read from the Word quote and from an older job details file, folder structure, renaming, subfolders copied, originals left in place, existing job refused, new range, missing range; all earlier PM, Points and Transform checks still pass.

## Build 1.18 — 2026-09-29
- **Several properties on one quote.** On the PM tab, Site Address, PID and Legal Desc. are now grouped as a property, with **+ Add another property** underneath; each extra property has its own address, PID and legal description and a ✕ to remove it. The Legal Desc. box is now full width and grows onto more lines. Quotes for one property look and work exactly as before.
- **Word quote:** with more than one property the teal bar reads "SITE ADDRESSES:" with the addresses stacked, one line per street — addresses that share a street and city share a line ("5864 & 5868 Pioneer Avenue, Burnaby", "5864, 5868 & 5872 …"). One property: unchanged.
- **Job details .txt and tracker row:** each label stays on one line, with the properties joined by " / " in order, e.g. "Site Address: 5864 Pioneer Ave, Burnaby / 5868 Pioneer Ave, Burnaby", and the same for Legal Desc. and PID (a blank in the middle shows as "—" so the order still lines up). Importing the file splits them back into properties; single-property files are unchanged.
- Sub-quotes, drafts saved inside the Word quote and reopening carry every property.
- Verified: add/remove properties, grouping by street, job details round trip exact, tracker row, Word files pass validation; all earlier PM, Points and Transform checks still pass.

## Build 1.17.3 — 2026-09-29
- **Job details: hours broken down by service.** When a quote has more than one service, Estimated Field Time and Estimated Draft Time keep the combined total on the first line and list each service's hours underneath, e.g. "   Topographic survey: 6.0 hrs 2 MAN CREW" / "   Posting plan: 3.0 hrs 2 MAN CREW". Optional and Option services are listed marked "(optional — not in total)" / "(option — not in total)"; a service with no field (or no office) hours is left off that line. Single-service quotes are unchanged. Import reads the new files (the hours still come from the Sublabour block) and older files open as before.
- **Word quote: cleaner fillable PDF.** Acrobat's Prepare Form auto-detect was making stray fields on every drawn line and box. The thin grey rule between services is gone (each service now has a little more space above it instead); the rule under the signatory is gone (more space before the contract instead); and the teal footer line is now a picture of the same line, which Acrobat ignores. The Site Address bar is unchanged. Only the Name, Phone #, Billing address, Date and Signature lines are left for Acrobat to find. **Upload the new quote-master.docx** with this build.
- Verified: per-service lines with included, optional and office-only services; job details round trip exact; files without the breakdown still import; Word file passes validation; all earlier PM, Points and Transform checks still pass.

## Build 1.17.2 — 2026-09-29
- Points tab fix: ticked fixes now always take effect even when an earlier fix on the same point is unticked. Before, if "Untick all" was used (or a fix such as trailing whitespace or underscores was unticked), any later ticked fix on that point — e.g. the imperial tree cm/m → ft conversion — was silently dropped, so the count read "0 points will change" and the downloads came out uncorrected. Each fix is now worked out from the text as it stands after the ticked fixes before it. A fix that depends on an unticked one (e.g. a tree code written with underscores) drops off the list until that one is ticked.
- Verified: ticking only the imperial conversions after Untick all changes exactly those points in the full cleaned file, corrections-only file and change log; all earlier Points, Transform and PM checks still pass.

## Build 1.17.1 — 2026-09-29
- **Open a quote (.docx or .txt)** on the PM tab (or drop the file on the tab). Every Word quote the app makes now carries the full draft hidden inside it — job details, every service card with its hours, scope lines (ticked and unticked), notes, blanks, status and price overrides, and the disbursements — in a standard custom-XML part that Word keeps when the file is opened and saved; the client never sees it. Opening that Word file brings the quote back exactly as downloaded, so a quote can be amended long after its draft has left the device. If the Word file was edited by hand afterwards, the app says so, lists the differences, and asks: take the services' text from the Word file (titles, scope lines, notes, prices; hours stay from the app) or open the app's version. Quotes made before this build have no draft inside; for those, open the job details .txt or start a new quote.
- **Duplicate as sub-quote**: copies the open quote as the next lettered sub-quote (26-586 → 26-586B, then C…), keeping client, site, job details and every service to trim with ✕; file name follows (Elev. Survey Quote 26-586B-Mark).
- **Unsaved quotes are marked**: a quote counts as saved once its Word quote or job details file has been downloaded since the last change. Unsaved drafts show NOT SAVED on their chip, with a count beside the drafts; deleting one warns that the draft will be lost.
- **30-day tidy, same rule as the checklists**: quotes saved and then untouched for 30 days are removed from the device when the PM tab opens, with a note saying how many; the downloaded files remain the record. Unsaved drafts are never removed automatically.
- Word quote signature block: each label now sits directly against its line ("Name: ____", "Phone #: ____", "Billing address: ____", "Date: ____", "Signature: ____") with more space under the contract, so Acrobat's Prepare Form auto-detect names the fillable fields from their own labels.
- Verified: reopening an app-made quote rebuilds the identical job details; a hand-edited copy (title changed, scope line added, price changed, re-zipped as Word saves) is detected and taken back correctly; older quotes are refused with a pointer to the .txt; sub-quote lettering; saved/unsaved marking, the 30-day tidy and the unsaved-delete warning; all earlier PM, Points and Transform checks still pass, and the Word files pass validation.

## Build 1.17 — 2026-09-28
- **Download quote (.docx)** on the PM tab builds the client quote in Word, on the 2023 letterhead, from the same services that drive the rate calculation. Built from a new template file, **quote-master.docx** (upload it next to index.html), with a clean layout: one two-column table (scope left, fixed right-aligned price column), numbered services with lettered scope lines that restart per service, Word styles for every part, services kept whole across pages, underline-tab signature blanks, no red text. Date (September 28, 2026), "Quote# 26-561", site bar, GST EXTRA, the disbursements line ("Disbursements extra at cost (1 title, 2 legal plans, 1 checklist fee): $155"), signatory and the acceptance contract fill in automatically. File name defaults to "Elev. Survey Quote 26-561-Jeff" (contact first name, else client) and can be changed. The template is cached so it also works offline after the first use.
- **Service cards replace the plain calculations.** Each card is one numbered service on the Word quote and one section of the job details calculation: pick a job type, and its approved title, scope lines and notes load; enter hours; the price is the calculation, or type over it (a number, "Hourly", "$90 per unit"). Each card is Included, Optional add-on (prints "Additional $X") or Option (prints "Option 1:", "Option 2:"); move up/down or remove.
- **Clause library** of 40 job types in 8 groups (topographic, property line, posting & reference plans, subdivision & legal plans, strata, construction & layout, certificates & as-builts, monitoring), with last year's sample wording restored. It lives in the encrypted vault and changes only through Finny. Lines to add only when they apply (Vancouver building envelope, White Rock average natural grade, Delta extras, additions/renos, Surrey as-built extra…) load unticked with the reason shown.
- **Fill-in blanks** such as "Final Strata plan for [building type]" (Duplex / Triplex / Fourplex / Six-plex / Townhouse complex or type your own), number of points, trips, lots, area. The quote can't be downloaded while a blank, the Quote #, client, site, signatory or a service price is missing; the reasons are listed.
- **Everything is editable per quote**: title, lead-in line, scope lines and notes (tick on/off, edit, add, reorder, remove), price text, and blank "Custom service" cards. Edits never change the library.
- **My saved versions**: "Save as my version" keeps a PM's own wording for a job type on their device; it appears under that job type as "Mine: …" beside the approved wording. Rename, delete, export and import to another computer under My saved versions.
- Job details file follows the cards: each card's title is its Sublabour section; Estimated Field/Draft Time and the totals count Included services only; Optional and Option services show their own subtotal marked "(optional — not in total)"; a typed price shows as "Posting plan Labour: $1,110.00 (quoted $1,200.00)" with "Total quoted" and Total before GST using the quoted prices. Import reads the markings and quoted prices back.
- Project Manager and PM initials carry over; drafts from 1.16 open unchanged as custom services.
- Verified: 26-561 and 26-562 rebuilt entirely inside the app, both passing Word file validation and matching the approved layout; blanks, options, optional add-ons, overrides, reordering, favourites and export/import; job details round trip exact; every earlier PM, Points and Transform check still passing.

## Build 1.16 — 2026-09-28
- New **PM** tab for building quotes. Locked behind a passphrase: the rates, disbursement prices, short role names and field crew instruction options live in a separate encrypted file, **pm-vault.json** (AES-256, key derived from the passphrase with 600,000 PBKDF2 rounds, all in the browser). Nothing about the rates is in index.html. "Remember on this device" skips the prompt on that device; Lock forgets it.
- **Locked by design.** Rates, disbursement prices, short names and the passphrase are view-only in the app — there is no way to edit them there. Changes are confirmed with Finny and arrive as a new pm-vault.json in the repo. The app always uses the repo's vault when online; the copy kept on the device is only an offline fallback, so a stale or altered local copy can never override the rates.
- **Job details form** in the order of the quote-26-000 template, plus Date requested and Assigned for the tracker. Quote # is required before the file can be saved; with it empty, the field is outlined red, the same rule as Job No. on checklists. **Project Manager and PM initials carry over**: once entered, every new quote on that device starts with them.
- **Rate calculation** with any number of calculations per quote (e.g. Topographic survey + Posting plan), hours per role with no minimums, a labour subtotal per calculation, disbursement counts (title, legal plan, checklist, filing fee, plus a free "other"), and the total before GST.
- **Download job details (.txt)**, named quote-26-561-job_details.txt, with Windows line endings. Hours are written as `6.0 hrs 2 MAN CREW`: one decimal, short uppercase role names (2 MAN CREW, 1 MAN CREW, LIDAR FIELD TECH, DRONE PILOT (PHOTO), DRONE PILOT (LIDAR), DRONE OFFICE TECH, CAD TECH, SENIOR CAD TECH, BCLS), in both the Estimated Field/Draft Time lines (totalled by role) and the Sublabour Calculation block (itemised per calculation). Copy job details and **Copy tracker row** (tab-separated, columns A–K of To Do Quotes) are also there, with a live preview.
- **Import job details (.txt)**: the Import button, or drop the file on the PM tab. It reads the header fields, crew instructions, notes (anything after the crew instructions, including trailing lines such as Rate source), disbursement counts, and hours from the Sublabour block — including the older wording (`6.0 hrs 2-man crew @ $220/hr`, `CAD tech`, `Senior Office Technician`) — with each calculation kept separate; if there's no Sublabour block it falls back to the Estimated Time lines. Anything it can't map is listed as "couldn't read — enter manually", and a rate in the file that differs from the current rate is pointed out. If a draft with the same Quote # already exists it asks whether to replace it or open the file as a separate draft. It also carries a draft between devices: save the .txt on one, import it on the other.
- Field Crew Instructions: pick one of the five standard topo options (1 Standard topo, 2 Topo with building details, 3 Full legal topo, 4 Typical Vancouver/Burnaby topo/post, 5 Topo for new laneway – Vancouver) and Insert, then edit freely, e.g. to fill in the [__cm] tree size. The options can be edited in the app under Rates & crew instructions; saved edits apply on that device straight away and download a pm-vault.json (same locked rates) to upload so every PM gets them.
- Drafts autosave on this device; each draft is a chip at the top with ✕ to delete.
- Verified: 26-561 (two calculations) and 26-562 reproduce their totals exactly ($3,107.50 and $1,640.00). Your 26-561, 26-562 and 26-000 files import with every field, calculation, hour line and disbursement read, and a file saved by the tab imports back identically. Also tested: wrong passphrase rejected, remembered unlock after reload, a newer local vault copy ignored in favour of the repo, offline fallback, option edits reaching another PM through the uploaded vault, and every other tab still loading.

## Build 1.15 — 2026-09-28
- Points tab: **Transform between drawings** — a new collapsible panel under Match points, for when two drawings of the same job are in different systems (e.g. a UTM-local drawing and the plan drawing) and you need to bring new points across. Pick From and To from the shelf; points are paired by identical point number (use Match points first when numbering differs).
- It fits four models at once — shift only, rotation + shift, scale + shift, scale + rotation + shift — shows each one's rms and max, and highlights the simplest that fits to within 3 mm. Scales are shown as grid → ground / ground → grid with the reciprocal, and are matched against any scale factor booked in either drawing (e.g. "exactly 1 / the factor booked on point 50 (BOOK73H0178 SF-0.99959126)"). Elevation offset is the mean dZ over points with elevations on both sides; points at 0 are ignored, and a varying dZ is flagged.
- When the whole set doesn't fit tightly it fits each numbering block separately and says so — e.g. control 1000–1009 scaled by 1/0.99959126 with +0.126 elevation, calc 1–28 by 1.00012383 — with a Fit on this block button. Fit on also takes a typed range (1000-1999, 1..28); individual common points can be unticked in the residual table.
- **Points to bring across** defaults to the points in From that aren't in To, or pick any shelf file and type point numbers (24_1,28_1). Output is the three values for MicroSurvey's Shift Coordinates → Shift using North/East/Elev, plus the Range of points to shift in MicroSurvey syntax, evaluated at the centre of those points with the worst-case error across them; a red note appears when one shift isn't good to 1 cm. Copy values button.
- Downloads: **Transformed points** (exact fitted model, only the selected points, source format and line endings kept, elevation-0 points left at 0 by default) and a **Transform log** with all four models, parameters, per-point before/after, and residuals.
- Verified on 26-3630: UTM-LOCAL vs PL packages (37 common points) — no rotation; control fits exactly at scale 1.00040892 = 1/0.99959126 with +0.126 elevation, calc points exactly at 1.00012383; 24_1 / 28_1 come out at North −1.368, East +0.638 (calc fit) or North −1.399, East +0.632, Elev +0.126 (control fit), matching the hand analysis.

## Build 1.14 — 2026-09-22
- Points tab **file shelf**. Every file you drop — .txt/.csv/.asc points files and .msz/.mbz drawing packages alike — is added to a shelf at the top of the tab instead of replacing what was there. The highlighted file is the one cleanup, extraction, and scale act on; tap another to switch, and each keeps its own ticks, manual rules, and scale settings while you do. Re-dropping a file with exactly the same name replaces that entry in place (marked ↻) — the "I re-exported after fixing codes in CAD" workflow. Each file has a ✕ to remove it; **Reset** clears the shelf.
- Match points picks each side from the shelf. The Second file buttons are gone: both the default Calc → tied-in mode and General mode show a source dropdown per side. With several files loaded the default mode proposes plan = the file with calc points and local = the file with control points, so a plan export plus a field file becomes drop, drop, Find. General mode with two different files on the sides takes all points of each unless you narrow with blocks or the control-codes filter; with one file on both sides it proposes the two far-apart blocks as before. Stages and Carry forward unchanged.
- Verified: 3621 (two text files) and 23-2362 (.msz) side by side on one shelf, switching between them, same-name replacement, single-file and cross-file matching, the three-set stages, remove and reset.
- Training tab: 18 videos that live directly in SharePoint as .mp4 (and so had no link file for the video pipeline) are now listed and clickable, each opening in the SharePoint player: the whole Elevate Office app folder (points matching, PL sample, points upload for crew), Automap (edit automap, process range linework), Area calculation (sliding bearing command), the beginner mp4s (3603 viewport and layout, PL sketch / import data / Helmerts, PDF .ctb print issue), the BCLS/PM mp4s (Survey Hub 2026 sign + register, monitoring Excel sheet, the three ChatGPT walkthroughs) with the Elevate system subfolder (job schedule, new draft, complete task + invoice), and "Using older drawings as base" at the root. 52 videos in 9 groups, plus a link to open the whole library. The obsolete folders are skipped.

## Build 1.13 — 2026-09-22
- Match points gains a **General** mode for stitching any two point sets; the default **Calc → tied-in** mode is unchanged. In General mode each side (A = reference, B = local) is picked from the file's numbering blocks — the tool proposes the two blocks that sit farthest apart, the usual sign of two coordinate systems — with an optional control-codes-only filter and a second file on either side.
- **Chained stages.** After any match, *Carry A + B forward* builds the combined set (B placed into A's system by the solved rotation and translation, matcher-internal only) and makes it side A for the next match. GPS → ground control, then ground + GPS → calc: two stacked results, each with its own pairs for its own Helmert. Start over clears the stages.
- **Monument-ID hints.** When the same monument number appears in descriptions on both sides (OCNT 5995 / OCNT 5995) those pairs seed the search and show ✓ID in the results. Where a coded ID disagrees with the figure — a shot coded OCNT 9999 that geometrically sits on OCNT 3314 — it's flagged ID≠ with an explanation, and IDs present on both sides but not paired by the figure are listed. Which control the crew tied, settled by evidence.
- Results now show descriptions on both sides, and a match with near-zero rotation and shift is labelled "same coordinate system". A faster pair-based engine handles larger sets (120 vs 90 points in about 150 ms); sets over 400 a side ask to be narrowed.
- Verified: the 3621 and 23-2362 defaults are byte-identical in behaviour; a synthetic three-set job (calc, ground control, GPS rotated 37.5° with one miscoded monument) resolves both stages correctly with the miscode flagged.

## Build 1.12.1 — 2026-09-21
- Save PDF to job file and Save as JSON now require a job number. With the field empty, nothing is written: the Job No. box is outlined red and focused with a note beneath the buttons, and the highlight clears as soon as you type. Prevents exports that can't be filed or found later.
- Points: Match points panel labels no longer run into their values, and the two Second file buttons line up.

## Build 1.12 — 2026-09-18
- Points tab: **Match points** — for the searches where it isn't apparent which found monument is which plan corner. Plan side = the file's calc points (1–99, CALC, blanks) or a second file; local side = the file's control-layer points (OCNT, OSPK, OLP, OIP…) or a second file, with each code shown as a chip so city control monuments can be excluded in a tap. Everything else in the file is ignored by the matcher.
- Method: matches the *figure* the points make — triangles with equal side lengths, same handedness — then tests each candidate pairing by fitting rotation + translation (never scale) and counting how many more points it explains; the pairing explaining the most points with the smallest residuals wins. Tries 5, 10, 15, then 20 cm, stops at the first solution, and reports which step it needed and whether the pairing stays stable when loosened to 30 cm.
- Output in the MS CAD Helmert layout (Local --> Plan, Vn, Ve, Dist, Direction), unmatched points on both sides (disturbed pins / monuments not found), and the rotation and translation as reference only. Copy pairs (`104 --> 7`) or the whole table; nothing is written to the change log — run the Helmert in MS CAD with the pairs you're confident in, as always.
- Scale is strictly diagnostic: if nothing fits at scale 1 but the figure would fit with one side converted, the tool says which side looks like feet and points at the Scale panel. It never scales anything itself.
- Verified on a real search (job 3621): 382-shot topo on assumed coordinates against 14 plan corners — nothing at 5 cm, solved at 10 cm with OLP 104 → 7, OLP 106 → 5, OIP 296 → 12 (residuals 3–6 cm, rotation 2.414°), stable to 30 cm; confirmed against the MS CAD Helmert. And on 23-2362: four found pins matched to calc corners at 5 cm in the same coordinate system.
- Scale about a point and Match points now sit as collapsible panels under the downloads, closed by default.

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
