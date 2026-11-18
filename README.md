0.54.0: record the review decision from the Pending row. UI only; no rule changes.
Constraints unchanged; no git; do NOT run --update-baseline. Verification: UI level
(ruff, tests for changed modules, browser tests -k pending and -k review only).
Design: board "Pending - review decision on the CRQ line".

1) Placement: on the CRQ line of each row awaiting approval, after the existing copy icon
   and "Remedy ↗" link: thin divider, small label "Review decision" (hidden below
   1280 px), then two icon-only buttons ✓ and ↻ (22 px high, fixed width). The Open
   column is unchanged. Scheduled/other statuses: no controls.
2) Visibility:
   - Not decided: label and both icons appear only on row hover or when the row (or a
     control in it) has keyboard focus; space is reserved so nothing shifts.
   - Decided: the filled icon (✓ green / ↻ amber) stays visible at all times; on hover or
     focus the label and the other icon appear so it can be changed.
   - Touch / no-hover devices (@media (hover: none)): controls always shown.
3) Behaviour: click records the decision; the chosen icon fills; click the filled icon
   again to clear. No text added to the buttons (line length never changes). Tooltips
   and aria-labels: "Approve CRQ…" / "Approved", "Needs work CRQ…" / "Needs work".
   Replaces the separate decision label on the CRQ line.
4) Same store as the Review overlay (one decision per change). Overlay -> Pending: rows
   update immediately when the overlay closes or moves with ‹ ›, without a reload.
   Pending -> overlay: shown when opened.
5) Row: green / amber left edge when decided. Status message above the table:
   "✓ Recorded for CRQ…: Approved · Undo" (existing message style); Undo restores.
6) Remove the existing "last opened / current overlay change" vertical line on Pending
   rows entirely, including its session state and CSS. Only the decision edge remains.
7) Above the table: segmented All · Not decided · Decided (filters the list; not in the
   URL), "Decided N of M" counting only changes awaiting approval, Copy decisions unchanged.
8) Keyboard: ↑/↓ row focus, A approve, N needs work, Enter open; visible focus ring.
9) Guide "The Pending page" one line; user-guide paragraph; CHANGELOG 0.54.0; pyproject
   0.54.0.
Tests: controls hidden at rest and shown on hover/focus for undecided rows; decided icon
visible at rest; always shown with hover:none; decide on Pending -> shown in overlay;
decide in overlay -> row updates without reload; clear and Undo; no width/height shift on
hover; Scheduled row has no controls; counter counts awaiting approval only; filter;
keyboard; no "last opened" line; row height unchanged at 1280 px. Report files and test
counts. Then stop.