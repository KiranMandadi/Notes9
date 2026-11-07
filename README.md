Pending table polish. Same standing rules; no git operations unless I ask.
1. Zebra rows: alternate rows get background #F8FAFC (others white). Apply to the list only, not the calendar; phone cards unchanged.
2. Last-closed row: keep only the 3 px navy (#0B1B33) left bar; remove its background tint so it works on both stripe colours.
3. Vertical alignment: top-align every cell in a row (align-items: start), with each column's first line on a common baseline: CRQ, window start, ORR value, risk level, score, and the Open button (nudge Open down so its text lines up with the first line).
4. Keep row hover off (rows aren't clickable). Check at 1440 and 1920 px with long summaries that wrap to 2 lines.
Update the browser tests and screenshots; CHANGELOG (no new version). Run the browser tests; report counts.
No branches, tags or commits.

git status
git add -A
git commit -m "Pending: clearer View by labels, Review Decision wording, only Open opens a report, zebra rows, top-aligned cells, bar-only last-closed marker"
git push