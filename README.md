UI refinements for the Tasks and Work detail panels (still 0.50.0). No data/rule changes.

PLACEMENT
- Move both panels INSIDE "Full change details", directly after "Plans", as rows in the same
  style as Plans/Relationships (chevron, title, count chip, grey description on the right):
  - "Tasks" · count chip "3" · description: "3 open · 0 closed · 0 cancelled"
    + amber pill "N need attention" only when N > 0.
  - "Work detail" · count chip "32" · description: "6 with notes · 1 attachment"
    + blue pill "1 exception on file" only when present.
  - Remove the separate cards above, and remove "Read live from Remedy · read-only" from both.
    (Full change details already says "As in Remedy, read just now".)
  - "Expand all" in Full change details also opens these two rows.
- Tasks: the open/closed/cancelled counts sit next to the title (as above), not on a separate line.

TASKS — expanded row
- Two-column label/value grid with a fixed label column (e.g. 120px) and values left-aligned on
  one vertical line: Task ID, Type, [Freeze check — tech only], Notes. "Notes" gets a label like
  the others. Notes keep Remedy line breaks (white-space: pre-wrap), wrap long words/URLs
  (overflow-wrap: anywhere), clamp to 5 lines with Show more.
- Remove the vertical line/border shown above/left of the expanded section; use one soft grey
  card (bg #F8FAFC, 1px #E6EBF2, radius 10, padding 14px 16px) aligned with the task name column.

WORK DETAIL
- Remove the "Notes" column. Columns: ▸ | Type | Added (ET) | Submitter (sortable as now).
- Top bar, LEFT: "Showing X of N" followed directly by the Type filter chip. RIGHT: Expand all.
- Type filter popover: "Select all" and "Clear" links at the top (same as Pending filters), a
  checkbox + full type name + count per type, wide enough that names are never cut (min 300px,
  wrap if needed). Active filter = teal outline.
- Rows with notes are expandable (chevron); rows without notes or Internal rows have no chevron.
- Expanded entry: same label/value grid as Tasks — Summary (only if it differs from the start of
  the notes), Notes (pre-wrap, wrap URLs, clamp 5 + Show more), Attachments (names), Source,
  View access. Do NOT repeat the summary as the first line of Notes.
- Remove the horizontal line shown above the notes inside an expanded entry; same grey card style.

Check at 100% and 110% zoom. Update the browser tests affected; run only the Review browser tests
and ruff. Report files changed and counts, then stop. No git.