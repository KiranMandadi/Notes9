git status
git diff --stat
git add -A
git status
git commit -m "0.50.0: Tasks, Work detail and Relationships panels on the Review page" -m "- Tasks and Work detail now inside Full change details (after Plans), read live from Remedy
- Tasks: Step (Remedy sequence; parallel steps muted), one-line rows, status (reason), group,
  scheduled with duration; Outside window / In freeze tags; Status and Group filters (shown when
  useful); sortable Status, Group, Scheduled; Needs attention only when > 0; expanded card with
  Task ID, type, summary, formatted notes
- Work detail: Type, Added (relative), Submitter on one line; Type multi-select filter; sortable;
  expanded summary/notes/attachment names; Internal entries' notes stripped server-side
- Relationships: table with Relationship and Request type filters, sortable columns
- Full change details: 'Description and notes' renamed to 'Summary and notes'
- Notes formatter (line breaks, separators, steps, labels, URLs as text) with unit tests
- Findings link to tasks (View task) and the At a glance Freeze row to exception work details
- Task Status Reason, task ID/type/summary/notes and work-info submitter read on Review only;
  all rows paged (no 200 cap); history.db unchanged; crq get strips Internal text and submitter
- Score footnote moved to a tooltip on the score ring
- Rule set unchanged (7066972d); docs, SECURITY.md, CHANGELOG and tests updated"
git push