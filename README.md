Task: Saved views on the Pending page (release 0.48.0), behind a feature flag.
Design (agreed, follow exactly): "Pending - saved views" board, steps 1–18.

=== HOW WE WORK ON THIS ===
STEP 1 (now): read the relevant code and reply with a PLAN only, then STOP:
  - files you will change/add
  - how the Pending filter state is held today (names of the state fields for ORR, Risk Level,
    Impact, Quality, Status, Class, Date, Organisation, Group, Approver, List/Calendar) and how
    you'll map them into a saved view — reuse the existing state, don't invent a parallel model
  - where the page gets settings from the server today (e.g. how REMEDY_CHANGE_URL_TEMPLATE
    reaches the page) and how the flag will follow the same path
  - how Default is built today, and the test list
STEP 2: implement only after I reply "go".

=== FEATURE FLAG ===
- New env setting: CHANGELENS_SAVED_VIEWS. Add to .env.example as:
    # Saved views on the Pending page (stored in each user's browser). true / false
    CHANGELENS_SAVED_VIEWS=false
- Read it in the Console server code (same pattern as REMEDY_CHANGE_URL_TEMPLATE). Do NOT touch
  or read cr_core/config.py. Only "true", "1", "yes" (case-insensitive, trimmed) = on; anything
  else, missing or malformed = off.
- Pass only a boolean to the page. Read at start-up (restart needed to change).
- crq doctor: add one line "Saved views: on" / "Saved views: off".
- Flag OFF: Pending looks and behaves exactly as today — no divider, no picker, no menu, no
  dialogs, and NO browser-storage reads or writes at all. Existing stored views are left
  untouched (hidden, not deleted).

=== PLACEMENT AND UI (flag ON) ===
- At the right end of the RISK row: thin 1px #DDE3EC divider (24px tall), label "VIEW"
  (same style as RISK/SCOPE labels), then the picker: 236px wide, 34px tall, radius 8,
  1.5px border #CFD7E3, icon ▦, view name (ellipsis + full name as tooltip), caret ▾.
- The whole group (divider, label, picker, Modified actions) stays together; if the Risk row is
  too full it wraps onto its own line, right-aligned. Never shorten chip text — ORR chip keeps
  "4 – Very High, 3 – High". Table, chips and dropdown labels unchanged.
- Modified: amber dot (7px #D97706) inside the picker, border #E8B266, then "Modified"
  (#8A4B08, 600) and actions: on Default → "Save as…", "Reset"; on a saved view → "Update",
  "Save as…", "Reset". Actions are real <button>s styled as links (Safari tab order).
- Menu (opens right-aligned under the picker, 360px): "Default" (with "system defaults"),
  divider, label "MY VIEWS · SAVED IN THIS BROWSER", views A–Z (case-insensitive) each with a
  one-line summary in short form, e.g. "Approver Rama Bokka · ORR 4, 3 · Risk Level 5, 4 ·
  Next 7 days" (summaries only — chips keep full text), divider, "＋ Save current as…",
  "⚙ Manage views…". Max height with scroll for 20 views.
- Save view dialog and Manage views dialog exactly as on the board (sizes, texts, colours,
  "This view will remember" tags, the ⓘ browser-only note, the Export note about approver names).
- Delete confirmation inline on the row (red text, Delete / Keep) — no nested pop-up.
- Rename inline on the row (Enter saves, Esc cancels).

=== WHAT A VIEW SAVES ===
Saved: Approver (a specific person or All approvers), ORR, Risk Level, Impact, Quality, Status,
Class, Date, Organisation, Group, layout (List/Calendar).
Never saved: search text, results/rows, review decisions, anything from Remedy.
Dates: presets saved as rolling (e.g. "Next 7 days" recalculated on open, in ET exactly as the
page does today — never the computer's own timezone). Custom ranges saved as fixed dates.

=== BEHAVIOUR ===
- Pending always opens on Default (today's system defaults). No user default view.
- Picking a view applies all its filters in one go (one load, not one per filter). If a load is
  in flight, the new one supersedes it. On-demand stages load with the existing status pill and
  progress cursor.
- Modified detection must have no false alarms: compare normalised filters — order-insensitive,
  every value ticked == "All", approver trimmed + case-insensitive, date preset vs preset.
  Refresh never sets Modified. "Show all approvers" / "Show only <name>" do.
- Reset = back to the selected view's saved filters (on Default = system defaults).
- Clear all = system defaults and the picker shows Default.
- Switching views while Modified discards changes without asking.
- Update = overwrite the selected view's filters (message). Save as from a saved view creates a
  new one; original unchanged; the new one becomes selected.
- Default can't be overwritten, renamed or deleted.
- Deleting the selected view (here or in another tab): keep filters on screen, picker shows
  Default + Modified.
- Undo after delete: 8 s; stays on the status line if Manage is closed. If the name is taken by
  then, restore as "<name> (restored)". Undo respects the 20 limit.

=== NAMES ===
- Normalise: Unicode NFC, trim, collapse internal whitespace. 1–40 characters (count code
  points). Reject control/format characters. "Default" is reserved (any case).
- Unique, case-insensitive (compare NFKC + lower-case). Changing only capitals on rename is
  allowed. Duplicate on Save as → inline warning + button "Replace view" (replace keeps the
  count, so it is allowed even at 20 views).
- Always render names as text (textContent), never HTML — in menu, dialogs, tooltips, messages.

=== LIMITS ===
- Max 20 views. At 20: Save as dialog shows the amber banner and the form is disabled (except
  Replace via an existing name). Import stops at 20 and reports skipped ones.

=== STORAGE (localStorage) ===
- One key: "changelens.views.v1" = {"version":1,"views":[{id,name,savedAt,filters}]}.
- IDs: do NOT use crypto.randomUUID (unavailable on plain http, which is how users reach the
  VM). Use crypto.getRandomValues-based ids.
- Wrap every read/write in try/catch. Always re-read the latest list immediately before any
  write (two tabs can't overwrite each other). Write the whole list in one setItem.
- Damaged/hand-edited data: parse safely, validate each view; keep valid ones, ignore bad ones,
  show one info message with the count. Never break the page.
- Build objects from known keys only (no __proto__/constructor copying).
- Missing filter in an old view → that filter's default. Values that no longer exist in config
  (org, group, status…) → dropped on open, amber message, view shows Modified.
- Storage blocked/unavailable (private mode, policy): picker shows Default greyed with ⓘ,
  Save as/Manage disabled, one info message per page load; everything else works.
- Write failure (quota/blocked): red message, nothing changed.
- navigator.storage.persist(): call only if available (secure contexts only); ignore failure.
- Other tabs: listen to the "storage" event for this key and refresh the menu/picker
  (rename/delete/save reflect immediately).

=== IMPORT / EXPORT ===
- Export: disabled when there are no views. Downloads changelens-views-YYYY-MM-DD.json
  (Blob + a[download]) containing {"app":"ChangeLens","type":"views","version":1,
  "exportedAt":ISO,"views":[...]} — filter choices only.
- Import: <input type=file accept=".json">. Don't trust the browser's MIME type (Safari/Firefox
  differ). Max 100 KB. Must be a ChangeLens views file; a newer version → refuse. Validate each
  view separately; skip invalid, duplicate names (vs existing and within the file) and anything
  over 20; drop unknown filter values. One summary message with counts and reasons.

=== MESSAGES (exact text) ===
Page-level ones use the existing status pill on the line above the table; Manage actions show
inside the Manage dialog. A new message replaces the previous one; never hide an active
Loading/Refreshing pill with a views message.
- ✓ View "{name}" saved in this browser            (green, fades ~4 s)
- ✓ View "{name}" updated / replaced / restored     (green)
- ✓ Renamed to "{name}"                             (green)
- View "{name}" deleted · Undo                      (info #EEF3FA, 8 s)
- View "{name}" deleted — filters kept on screen · Undo   (when it was selected)
- ✓ Exported N views                                 (green)
- ✓ Imported N views · M skipped ({reasons})        (green; reasons: name already exists,
                                                       20-view limit, not valid)
- ⚠ Couldn't read this file — it isn't a ChangeLens views file. Nothing was changed. (red)
- ⚠ This file was made by a newer ChangeLens. Nothing was changed.                   (red)
- ⚠ This file is too large (max 100 KB). Nothing was changed.                        (red)
- ⚠ Couldn't save the view — browser storage is full or blocked. Nothing was changed. (red)
- ⚠ N saved filter value(s) no longer exist and were skipped ({Field}: {value})     (amber)
- ⚠ This view's date range ({d}–{d} {Mon}) has passed — pick a new Date or Update the view (amber)
- ⓘ Saved views aren't available in this browser. Everything else works as usual.  (info, once)
- ⓘ N saved views couldn't be read and were ignored.                               (info, once)
- Limit banner: "You have 20 views, the most this browser keeps. Delete one in Manage views to
  save another."
- Safari only (detect Safari, not Chrome/Edge/Firefox on Mac): amber line in Save view and
  Manage views: "Safari may clear saved views if you don't open ChangeLens for 7 days — use
  Export to keep a copy."

=== BROWSERS AND ACCESSIBILITY ===
- Current Chrome, Edge, Firefox, Safari on Mac and Windows. No APIs those don't all support;
  feature-detect anything secure-context-only (the VM is plain http).
- Menu: keyboard (arrows, Enter, Esc), click-outside closes, focus returns to the picker.
- Dialogs: role="dialog", aria-modal, labelled; focus trapped; Esc closes; name field focused
  on open; Save disabled while saving (no double-create).
- Under prefers-reduced-motion: no fades.
- Check the Risk-row wrap at 100% and 110% zoom, at 1280px and 1496px widths.

=== SECURITY / DATA ===
- Views never go to the server, the URL or any log. Approver and search text never in the URL.
- No caching of Remedy data; rows always load live.

=== RELEASE ===
- Bump the version to 0.48.0 wherever previous releases bumped it.
- CHANGELOG: 0.48.0 — "Saved views on the Pending page (flag CHANGELENS_SAVED_VIEWS, off by
  default): save, update, rename, delete with undo, import/export; stored in each user's
  browser."
- docs/user-guide.md: short "Saved views" section, including: "Views are saved in the browser
  you use; use Export to move them to another computer (also before the Console moves to a new
  address)." Mention the flag in the admin/setup docs.
- Rules/scoring unchanged: do NOT run --update-baseline.

=== TESTS (tiered — not the full gate) ===
- Put pure logic (normalise names, normalise/compare filters, validate stored data and import
  files, build summaries) in one small module and unit-test it via the browser tests.
- Browser tests (Chromium): flag off = no picker and zero localStorage access; flag on =
  default open, apply view, Modified on/off (incl. order-insensitive and All-equivalence),
  Update/Save as/Replace/Reset/Clear all, rename rules, delete + undo (+ "(restored)"),
  delete selected view, 20 limit (+ replace allowed), damaged storage, storage blocked,
  write failure, two tabs (storage event), import (valid, bad, too large, newer version,
  duplicates, over limit, unknown values, __proto__ keys), export content, value-gone message,
  past custom dates, rolling preset in ET, names rendered as text, keyboard in menu/dialogs.
- If Playwright's Firefox and WebKit browsers are already installed, also run the saved-views
  tests on them; do not install anything without asking.
- Run the existing Pending browser tests to confirm nothing else changed (K12 at 390px is a
  known failure).
- Report: files changed, tests run, pass/fail counts. Then stop for my review.

=== STANDING RULES ===
- Never read, search or print cr_core/config.py, cr_core/history/config.py or .env.
- No git commands. No inline Python (no python -c). Don't run --update-baseline. Never run
  crq login. Don't use search-and-replace tools that rewrite whole files; edit precisely.
- Replies: codes and counts only.