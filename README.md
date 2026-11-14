Alignment and one-line rows (0.50.0). Items 1–3 were requested earlier and are still visible:
verify with a browser screenshot at 100% and 110% zoom before reporting.

1) Work detail grid: columns 28px | Type minmax(220px, 1.2fr) | Added minmax(260px, 1fr) |
   Submitter minmax(200px, 1fr), gap 16px. The header row uses the SAME grid template as the
   data rows. Cells: min-height 40px, no top margin or padding offsets, so Type, Added and
   Submitter share one baseline. Type and Submitter: never truncate or use ellipsis — full text,
   wrapping onto a second line if needed; the other cells stay on the first line's baseline.

2) Controls bar inside Tasks and inside Work detail = a single flex row
   (display:flex; align-items:center; justify-content:space-between; gap 12px):
   left group (Show segment, or "Showing X of N" + Type chip), right group (Expand button).
   No separate wrappers with their own margins; the button must not sit higher than the left
   group.

3) Rows in Full change details (all rows, incl. Tasks and Work detail): the title, count chip,
   pills and right-hand description sit in ONE flex row with align-items:center. The description
   must not be absolutely positioned or have its own top offset.

4) Step connector with expanded tasks: the expanded card starts after the Step column (left edge
   aligned with the Task column), and the connector for a same-step group runs continuously down
   the Step column alongside any expanded card, until the last task of that step. If the expanded
   task is the last in its step, the connector ends at that task's row and doesn't continue down
   the card. No gaps or cut lines when expanding or collapsing.

5) Task rows on ONE line wherever the text fits (same grid approach as Work detail;
   min-height 40px):
   - Status: "Staged (Staging in Progress)" — the bracket part muted #8592A8; no second line.
     Cancelled: "Closed (Cancelled)", greyed as now.
   - Scheduled: multi-day "Mon 16 Nov 20:30 → Tue 17 Nov 07:00 (10 h 30 min)"; same day
     "Mon 16 Nov · 20:30–23:00 (2 h 30 min)"; duration in brackets muted. Remove the relative
     hints ("in 2 days", "started", "date has passed"). "No scheduled dates" (amber) and "—"
     (cancelled) unchanged.
   - Tags "Outside window" / "In freeze" (and the tech-only counted tags) sit inline after the
     task name, same line.
   - Long task names, groups and statuses: never truncate or use ellipsis — show the full text
     and let it wrap onto a second line when needed (overflow-wrap: anywhere). Cells in that row
     align to the first line (align-items: start with matching padding), so short cells stay on
     the first line's baseline.
   - Columns: 28px | Step 48px | Task minmax(0,2fr) | Status minmax(0,1.2fr) |
     Assigned group minmax(0,1.2fr) | Scheduled minmax(300px,1.4fr).

Add browser tests that check:
- these elements share a vertical centre (±2px): the Work detail header cells; the controls bar
  left and right groups; the Full change details title and description;
- expand a middle task of a 3-task step: the connector is continuous (no gap > 1px);
- a task row with short text is a single line (row height ≤ 44px); a task with a very long
  name wraps fully with no ellipsis, and the other cells stay on the first line's baseline;
- the scheduled text has no relative hint;
- no element in the Tasks or Work detail tables uses text-overflow: ellipsis.
Update the date-format tests for the new task format. Run the Review browser tests and ruff only.
Report files and counts, then stop. No git.