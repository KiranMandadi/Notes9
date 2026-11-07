Two Pending changes. Same standing rules; no git operations unless I ask.

1. Decision pill text: "Review Decision: Approved" / "Review Decision: Needs work" (same icons, outlined style and colours), also in the calendar tooltips and phone cards; on phones it may wrap below the CRQ. Overlay buttons, Copy Decisions and stored values unchanged.

2. Rows are no longer clickable:
   - Remove the row click handler, its role/tabindex, "Open report for …" row label and Enter-on-row behaviour; only "Open →" opens the overlay (Ctrl/⌘-click still opens a new tab).
   - Default cursor on rows; text can be selected freely.
   - Remove the row hover background. Keep the copy icon appearing on row hover and on keyboard focus of the CRQ; clicking it copies without opening anything.
   - Keep the last-closed row highlight (background and navy left bar).
   - Calendar bars stay clickable. Phone cards: only the Open button opens.

Update tests (row click does nothing; Open opens; copy icon on hover copies without opening; text selection works) and the user guide, decisions.md and CHANGELOG (no new version). Run the browser tests; report counts. No branches, tags or commits.


git status
git add -A
git commit -m "Pending: remove Viewed marks; Review Decision pill wording; only Open opens a report"
git push