Task: Review page — Tasks and Work detail panels (release 0.50.0). Read-only, live Remedy only.
Design (agreed, follow exactly): boards "Review - tasks panel" and "Review - work detail panel".

=== STEP 1: PLAN ONLY, then STOP ===
Files to change, how the Review request reads TMS:Task and CHG:WorkLog today, how you'll add
fields without affecting the batched Pending read, how paging will work, and the test list.
Wait for my "go".

=== DATA (live only — history.db, history_map.yaml and replay do NOT change) ===
Add to remedy_field_map.yaml and the models as OPTIONAL fields, read ONLY on the single-change
Review request (not the batched Pending/summary reads; no extra Remedy calls beyond paging):
- TMS:Task: task ID (Task ID), task type (TaskType), summary (Summary), notes (Notes).
  Already read: sequence, name, status, status reason, group, scheduled start/end.
- CHG:WorkLog: submitter (Work Log Submitter), source (Communication Source),
  view access (View Access), attachment names (z2AF Work Log01–03 / FileNameAttachment1–3 —
  confirm which is filled; names only, never download, never sizes).
  Already read: type, summary (Description), notes (Detailed Description), date, attachment count.
- Paging: on Review, read ALL task and work-info rows (page like Pending does) instead of the
  unsorted 200 cap. If a hard safety cap remains, sort newest-first in the Remedy query and
  show "Showing N of M".
- Submitter is a person: display only — never logged, stored, cached, exported to history or
  written to any file. Keep it out of history (people_fields already blocks it).

=== INTERNAL WORK INFO (security) ===
For entries whose View Access is Internal: the SERVER removes notes and attachment names before
sending to the browser (they must not appear in the API response). The row shows type, date,
submitter; notes cell shows a muted "—"; the row is not expandable. No explanatory text.
Rules are unaffected (they use the entry type only).

=== TASKS PANEL (below Findings) ===
- Collapsed by default. Header: "TASKS · N", "a open · b closed · c cancelled", amber pill
  "N need attention" when any task has a problem tag, right: "Read live from Remedy · read-only".
- Open: count line; "Show: All · N / Needs attention · N" segment; "Expand all/Collapse all".
- Columns: ▸ | # (sequence) | Task (name + tags) | Status (status, reason below) |
  Assigned group | Scheduled (ET).
- Default order: sequence. Sortable: Status, Assigned group, Scheduled (ET) only — click cycles
  ▲ asc → ▼ desc → back to sequence; active header teal #0B5F59, others faint ↕; ties keep
  sequence; tasks without dates go last when sorting by Scheduled.
- Calm dates: same day → "Tue 17 Nov · 20:00–23:00"; multi-day → "Tue 17 Nov 20:00 → Wed 18 Nov
  02:00"; second line: duration + hint ("in 3 days", "today", "started", "date has passed" in
  amber, "cancelled"). No dates → "No scheduled dates" in amber.
- Problem tags (always shown, shared 11px pill style): "Outside window" (#FDF0DC/#8A4B08),
  "In freeze" (#FDE8E7/#7A1212), "No dates" (#FDF0DC/#8A4B08) — derived from the same
  CC-05/CV-09/CV-13 results, never recomputed differently.
- Technical details ON only: "Implementation · counted" / "Certification · counted"
  (#E8F3F2/#0B5F59), "Not counted" (#EEF1F6/#475569), legend line, and in the expanded row a
  "Freeze check" line explaining why (inside window / stale / no valid dates / cancelled /
  not a reference task); rule codes prefixed on problem lines and finding titles.
- Cancelled, bypassed and rollback tasks greyed (opacity .6).
- Expanded row (grey card): Task ID (mono), Type, [Freeze check — tech only], Summary/notes
  clamped to 5 lines with "Show more/Show less"; amber problem line when the task has a finding.
  No actual start/end. No assignee — group only.

=== WORK DETAIL PANEL (directly below Tasks) ===
- Collapsed by default. Header: "WORK DETAIL · N", "Latest {date · time}", soft blue pill
  (#EEF3FA/#1C3358) "1 exception on file" when a Restriction Exception / Restriction Approval
  Notes entry exists; right: "Read live from Remedy · read-only".
- Open bar: "Showing X of N"; Type filter chip "Type All ▾" (multi-select popover with
  checkboxes, per-type counts, Select all / Clear; active = teal outline; label = type name /
  "N selected" / "None"); "Expand all".
- Columns: ▸ | Notes | Type | Added (ET) | Submitter.
- Notes cell: first 2 lines of the notes (clamped). Show the summary in bold above ONLY when it
  differs from the start of the notes (normalise whitespace/case before comparing).
- Sortable: Type, Added (ET), Submitter — default Added newest first; click toggles ▲/▼;
  Type/Submitter start A–Z; ties newest first. Works with the Type filter.
- Added: "Mon 16 Nov · 14:20" + relative ("2 days ago").
- Expanded: full notes clamped to 5 lines with Show more; attachment NAMES as small chips (no
  sizes, no links); Source; View access. Tech only: "Used by: CC-05 · exception" where relevant;
  exception tag reads "Exception · used by CC-05" (tech) / "Exception" (off).
- Footer: "Click Type, Added or Submitter to sort · submitter names are read live from Remedy
  and never stored."

=== FINDINGS LINKS ===
- CV-13 / CC-05 / CV-09 findings that name a task get "View task NN ↓": opens Tasks, resets
  "Show" to All, expands and highlights that row (amber left bar #D97706, bg #FFFBF4).
- A CC-05 finding cleared by an exception gets "View work detail ↓": opens Work detail, resets
  the Type filter to All, expands and highlights the entry (navy left bar #1C3358, bg #F5F8FD).

=== COMMON ===
- All text rendered as text (never HTML). Long group/type names ellipsis + full text on hover.
- Loading: 3 skeleton rows; errors use the existing status pill style; empty: "No tasks on this
  change." / "No work detail on this change."
- Keyboard: rows and headers are buttons (Enter/Space), aria-expanded on rows, aria-sort on
  sortable headers. prefers-reduced-motion respected.
- Print/PDF: both sections print expanded, without controls.
- Pending, rules, scoring and history are unchanged. Rule set id must NOT change.

=== TESTS (tiered) ===
Contract tests: new optional fields; Internal entries have notes/attachment names removed in
the API response; submitter never in logs/history; paging beyond 200. Browser tests: collapsed
default, expand/collapse all, sort cycles (tasks 3-state, work detail toggle), Type filter
multi-select, tech toggle shows/hides counted tags and codes, View task/View work detail links,
Show more, calm date formats incl. multi-day and no dates, Internal row not expandable.
Run those + ruff + the Review browser tests. Not the full gate. Confirm rule set id unchanged.

=== RELEASE ===
0.50.0, CHANGELOG, user guide (Tasks and Work detail sections), SECURITY.md (Internal work info
stripped server-side; submitter display only).

=== STANDING RULES ===
Never read/search/print cr_core/config.py, cr_core/history/config.py or .env. No git. No inline
Python. Don't run --update-baseline. Never run crq login. Codes and counts only. Report files
changed and counts, then stop.