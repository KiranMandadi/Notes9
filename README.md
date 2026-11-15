Task: new "Guide" page in the Console (release 0.51.0). UI + config flag + docs only.
No rule, data or scoring changes; the rule set id must NOT change.

=== STEP 1: PLAN ONLY, then STOP ===
Files to change, how the nav/routes and the existing flag (CHANGELENS_SAVED_VIEWS) are wired,
where the scoring weights/thresholds live in config, and the test list. Wait for my "go".

=== FEATURE FLAG ===
- New env setting CHANGELENS_GUIDE, default ON. Add to .env.example:
    # Show the Guide tab in the top navigation. true / false
    CHANGELENS_GUIDE=true
- Read it in the Console server code exactly like CHANGELENS_SAVED_VIEWS (do NOT touch
  cr_core/config.py). Missing or empty = ON. Only "false", "0", "no", "off" (trimmed,
  case-insensitive) = OFF.
- OFF: no Guide tab; ?page=guide opens the Review page instead. ON: tab and page available.
- crq doctor: add "Guide: on" / "Guide: off".

=== PLACEMENT ===
- Fourth tab in the main nav after Rules: "Guide". Route ?page=guide. Same header, footer and
  Technical details toggle as other pages. No links to the Guide from any other page.
- Static content only: the page makes NO calls to Remedy and shows no real changes or people.

=== HEADER (navy band, like other pages) ===
Eyebrow "GUIDE"; title "How to use ChangeLens"; one line: "ChangeLens checks change records
against agreed rules, live from Remedy and read-only. This page explains the quality report and
the Pending page." No contents/jump-link row.

=== SECTIONS (white cards, gap 24px, eyebrow "0N · …" + 20px semibold title) ===

01 · Reading a report — title "Parts of the report"
Left: a static miniature report built from the real Console CSS (no images): navy header with
"CRQ000002491234", "Promote DB2 stored procedures · Tue 17 Nov 20:00 ET" and a score ring "75"
(amber); left column: verdict box "Needs work · Set the scheduled times of every open task.",
issues box (Major "Open tasks have no scheduled dates", Minor "Window longer than 8 h"),
past-changes line "Past changes · 42 similar · Usually starts 21:00 · Window 2× the usual ·
Approvals ~3 days", details line "Summary and notes · Tasks · Work detail · Relationships";
right column: At a glance (Class · Normal, ORR · 4 – Very High, Freeze · No clash,
Lead time · 18 days).
Six numbered hotspots (22px circles) on the miniature, and a matching list on the right.
Clicking a hotspot or a list row selects it (one open at a time); the open row shows its text:
1 Score — "Starts at 100 and drops with each issue according to its severity. The ring colour
  matches the verdict."
2 Verdict — "Ready, Needs work or Blocked, followed by the most important fix in plain language."
3 Issues to fix — "Listed by severity, highest first. Each issue states what is missing and how
  to fix it. Advisories are shown but not scored."
4 Compared with past changes — "Context from similar past changes of the same product: the
  usual start time, typical window length, how long approvals take and whether incidents
  followed. Provided for context only; it does not affect the score."
5 At a glance — "Key facts for approval: class, risk, freeze, lead time and overlapping changes."
6 Full change details — "Summary and notes, tasks, work detail and relationships — read live
  from Remedy, so opening Remedy is rarely needed."

02 · Scoring — title "How the score is calculated"
Left: "Every change starts at 100; each issue deducts points by severity. Adjust the counts
below to see the effect on the score and verdict." Rows Blocker / Major / Minor / Advisory with
their colour pills, "−40 each"/"−20 each"/"−5 each"/"No points" and − / + steppers (0–5).
Right: score ring (conic, colour by verdict), verdict pill, the sum in mono
("100 − 20 − 5 = 75"), and the line "Ready 85+ · Needs work 40–84 · Blocked <40 or any Blocker".
WEIGHTS AND THRESHOLDS ARE READ FROM THE RULE CONFIG (the same values the engine uses), never
hard-coded; the labels above are generated from them.

03 · Working through Pending — title "The Pending page"
Static miniature of Pending (navy header "Srinivas Sasapu · 2 changes" — use a neutral sample
name "A. Approver" instead; List|Calendar; Refresh), Risk/Scope chip rows, a status message,
"Review decisions · Decided 0 of 1 · Copy", and a one-row table with "Showing 1 of 2" and
"1 hidden by ORR · Show all". Six hotspots + list, same interaction as 01:
1 Whose changes — "Opens on the configured approver, even when nothing is waiting. Show all
  approvers widens the list to everyone; the Approver filter narrows it again."
2 Risk and Scope filters — "Filter by ORR, Risk Level, Impact, Quality, Status, Class, Date,
  Organisation, Group and Approver. Active filters show a teal outline; Clear all restores the
  defaults."
3 Saved views — "Save the current filters under a name and reapply them at any time. Views are
  stored in the browser on that computer; Export keeps a copy." (Show this hotspot and its
  picker in the miniature ONLY when CHANGELENS_SAVED_VIEWS is on; renumber when hidden.)
4 Status and decisions — "Loading, refresh and error messages appear on the left. On the right,
  record Approve or Needs work for each change and use Copy Decisions to share them."
5 The table — "Sorted by ORR, then risk, then start time; select a column header to re-sort.
  A grey label shows how many rows the filters hide, with Show all."
6 List or Calendar — "Calendar shows the same changes by day, with freeze periods marked.
  Refresh reloads the data from Remedy."

04 · Questions — title "Frequently asked questions" (accordion, +/−, one open at a time):
- Why is a change Blocked? — "The change has at least one Blocker, such as a missing backout
  plan or work scheduled in a freeze without an approved exception, or its score is below 40.
  The verdict names the first issue to fix."
- Is the data live? — "Yes. Each page reads Remedy when it is opened or refreshed. ChangeLens
  never writes to Remedy and does not cache change data."
- Why is a change missing from Pending? — "A filter is excluding it. The grey label above the
  table shows how many changes are hidden and by which filter; Show all brings them back."
- Where are saved views stored? — "In the browser on the computer where they were saved. Export
  in Manage views keeps a copy or moves them to another computer." (only when saved views on)
- What if a finding looks incorrect? — "Turn on Technical details to see the rule code and the
  evidence it used, then report it. Rules are tested against thousands of past changes."

05 · Terms — title "Glossary":
ORR — "Operational Readiness Rating: how critical the application is, from 4 – Very High to
1 – Low." · Risk Level — "The risk recorded in Remedy for the change, from 1 to 5, based on the
risk assessment questions." · Freeze — "A restricted period. Implementation and certification
tasks scheduled inside it block approval unless an approved exception is recorded." ·
Advisory — "A point worth reviewing; it does not affect the score." · Stale task — "A task
scheduled entirely outside the change window, usually left over from a reschedule." · Step —
"The task sequence from Remedy. Tasks with the same step run in parallel."

06 · Data — title "Data handling": four equal tiles in one row (2×2 below 1100px), each with a
small teal ✓, bold title and one line: Read-only — "Nothing is written to Remedy." · Live —
"Change data is read on demand and not cached." · No personal data — "No personal data is
stored in history." · Internal notes — "Internal work notes are not shown."

=== STYLE ===
Same fonts, colours and card style as the Console (cards #fff, 1px #E1E6EE, radius 14;
eyebrow 11px uppercase #5B6880; teal #0E7C74). Neutral, professional voice: never "you"/"your";
instructions in plain imperative. All text as text nodes. Keyboard accessible (buttons,
aria-expanded/aria-pressed); works at 100% and 110% zoom and down to 1024px; no external
assets; prefers-reduced-motion respected.

=== TESTS & RELEASE ===
Browser tests: flag on → tab and page; flag off → no tab and ?page=guide shows Review; missing
flag = on; hotspot ↔ list sync in 01 and 03; simulator maths and verdict match the real config
(any Blocker → Blocked, <40 → Blocked, ≥85 → Ready); saved-views hotspot/FAQ hidden when that
flag is off; FAQ accordion; no network request to Remedy from ?page=guide; no "you"/"your" in
the page text. Run those, the nav tests and ruff only.
Version 0.51.0; CHANGELOG; user guide + admin docs mention CHANGELENS_GUIDE. Confirm the rule
set id is unchanged. Report files changed and counts, then stop.

=== STANDING RULES ===
Never read/search/print cr_core/config.py, cr_core/history/config.py or .env. No git. No inline
Python (no -c, no stdin). Don't run --update-baseline. Never run crq login. Codes and counts only.