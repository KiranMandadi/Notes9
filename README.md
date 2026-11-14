Tasks fixes + Relationships table (0.50.0). UI only. Verify every item with a browser screenshot
at 100% and 110% zoom before reporting — items 3 and 4 were requested twice and are still visible.

1) Step column — remove the drawn connector line entirely. Instead:
   - show the step number on every row; when it equals the previous row's step (in sequence
     order), render it muted #B9C3D3;
   - no row divider between rows of the same step; keep the 1px divider between different steps;
   - expanded cards don't change this.
   When sorted by another column, show all numbers in normal colour with dividers on every row.

2) Scheduled always on one line: white-space: nowrap for the scheduled text, including the
   "(10 h 30 min)" part. Columns: 28px | Step 48px | Task minmax(0,1.6fr) |
   Status minmax(0,1.1fr) | Assigned group minmax(0,1fr) | Scheduled minmax(360px,auto).
   Task, Status and Group still wrap fully when long (no ellipsis).

3) Rows in Full change details (Tasks, Work detail, Relationships and all others): title, count
   chip, pills and the right-hand description in ONE flex row, align-items:center. Remove any
   separate wrapper, absolute positioning or top offset on the description.

4) Controls bar in Tasks, Work detail and Relationships: ONE flex row, align-items:center,
   justify-content:space-between; left group = Show / Showing + filters; right = expand button
   (Relationships has none). The button must share the vertical centre of the left group.

5) Relationships as a table:
   - Keep "Affected services" at the top as now.
   - Controls bar: "Showing X of N" + filter chips "Relationship All ▾" and "Request type All ▾"
     — same component as the Work detail Type filter (multi-select checkboxes, counts,
     Select all / Clear, max-height 320 with scroll, never clipped, teal outline when active).
   - Table grid (header row uses the same template): Relationship minmax(120px,0.8fr) |
     Request type minmax(150px,0.9fr) | Request summary minmax(0,3fr) | Status
     minmax(100px,0.6fr). Header cells and data cells share one baseline; summary wraps fully,
     other cells stay on the first line; row dividers 1px #EEF1F6; row padding 10px.
   - Sortable: Relationship, Request type, Status (click toggles ▲/▼, same style as other
     tables; ties keep Remedy order). Default order = Remedy order.
   - Empty state when filters match nothing: "No relationships match the filters · Select all".
   - Text only (no links), as today.

Browser tests: the same-step rows have a muted number and no divider; scheduled text is one line
at 1280px and 1496px widths; the alignment checks (±2px) for items 3 and 4; the Relationships
filters (multi-select, Select all/Clear, counts), sorting and empty state. Run the Review browser
tests and ruff only. Report files and counts, then stop. No git.