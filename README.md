Remove "Viewed" from Pending completely. Same standing rules; no git operations unless I ask.
- Remove the "✓ Viewed" text and its "·" separator from the CRQ line, the phone cards, and the calendar bars (✓ mark and "Viewed" in tooltips).
- Remove the Viewed tracking itself: its sessionStorage key, the code that records opens, and any reads of it. Keep the separate decisions store unchanged.
- Keep the last-closed row highlight (background and left navy bar).
- The CRQ line becomes: CRQ number, copy icon on hover, then the decision pill only when a decision exists (no leading separator).
- Remove or update every related test; update SECURITY.md (remove Viewed from what's kept in the tab), the user guide, decisions.md (Viewed removed: decisions and the row highlight cover it) and CHANGELOG (no new version).
- Run the browser tests and `python scripts/check.py --browser --audit`; report counts.
No branches, tags or commits.

git status
git add -A
git commit -m "Pending: remove Viewed marks; decisions and the last-closed highlight cover it"
git push