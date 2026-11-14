Alignment fixes (0.50.0). Items 1–3 were requested earlier and are still visible: please verify
with a browser screenshot at 100% and 110% zoom before reporting.

1) Work detail grid: columns 28px | Type minmax(220px, 1.2fr) | Added minmax(260px, 1fr) |
   Submitter minmax(200px, 1fr), gap 16px. The header row uses the SAME grid template as the
   data rows. Every cell (headers and rows): display:flex; align-items:center; min-height 40px;
   no top margin or padding offsets, so Type, Added and Submitter share one baseline.

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

Add browser tests that check:
- these elements share a vertical centre (±2px): the Work detail header cells; the controls bar
  left and right groups; the Full change details title and description;
- expand a middle task of a 3-task step: the connector is continuous (no gap > 1px).
Run the Review browser tests and ruff only. Report files and counts, then stop. No git.