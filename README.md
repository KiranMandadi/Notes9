Tasks filters (UI only).
- Add filter chips to the Tasks controls bar, same component as the Work detail Type filter
  (multi-select checkboxes, per-value counts, Select all / Clear, label/value styling, teal
  outline when active, max-height 320 + scroll, never clipped):
  "Status All ▾" (values = status, e.g. Staged / Closed / Pending; Closed-cancelled shown as
  "Closed (Cancelled)") and "Group All ▾" (assigned group).
- Show a chip only when its column has 2+ distinct values; hide both chips when the change has
  5 tasks or fewer.
- Bar layout (one flex row): left = "Showing X of N" · Status · Group · Show segment (only when
  need-attention > 0); right = expand button.
- Filters combine with the Show segment and with sorting; Step muting/dividers use the visible
  rows. Empty state: "No tasks match the filters · Select all" (resets both filters and Show).
- "View task NN ↓" from a finding resets all task filters to All before opening the row.
Browser tests: chip visibility rules (≤5 tasks, single value), multi-select, counts, combination
with Show, empty state, View task reset. Run the Review browser tests and ruff only. Report
files and counts; then stop. No git.