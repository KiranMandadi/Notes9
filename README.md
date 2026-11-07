Pending View by labels. Same standing rules; no git operations unless I ask.
- Tabs: "Operational Risk Rating (ORR)" | "Risk Level" | "Impact" | "Quality" (rename "Risk" → "Risk Level", "Readiness" → "Quality"; Impact unchanged).
- Caption: "Grouped by ORR" / "Grouped by risk level" / "Grouped by impact" / "Grouped by quality".
- Compact sticky header breadcrumb uses the same names.
- Keep the URL values unchanged (view=orr|risk|impact|readiness) so existing links still work.
- Card values unchanged; table column headers unchanged.
- Check the tab row fits on one line at 1280 px and wraps cleanly on phone.
- Update tests, user guide and CHANGELOG (no new version). Run the browser tests; report counts.
No branches, tags or commits.

git status
git add -A
git commit -m "Pending: remove Viewed; Review Decision pill wording; only Open opens a report; clearer View by labels (Operational Risk Rating, Risk Level, Impact, Quality)"
git push