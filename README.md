Pending decision placement, back-to-top everywhere, report column balance. Same standing rules: no git operations unless I ask; never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env; live data only; no rule, score, finding or status changes; codes and counts only in replies.

1. Pending Change cell:
   - Remove the DECISION row from the label grid; the grid keeps PRODUCT only.
   - Show the decision on the CRQ line after "✓ Viewed", separated by a muted "·": "CRQ000002480998  ✓ Viewed · ✓ Approved". Use the existing outlined decision pill style (12 px).
   - Show it only when a decision is made; no "Not decided" text anywhere in the row. If the change isn't viewed but has a decision, show only the decision pill (no leading separator).
   - Same in the phone cards. The calendar dots and tooltips, "Decided N of M" and Copy Decisions are unchanged.

2. Back to top, as one shared component:
   - A round button, bottom-right, 40 px, white with a #CFD7E3 border and a soft shadow, an ↑ icon, aria-label and tooltip "Back to top".
   - It appears after scrolling more than one viewport height and hides near the top. Smooth scroll, or instant under prefers-reduced-motion. Focus moves to the page's main heading afterwards.
   - Use it on Pending (replace the existing one), Rules, the standalone Quality report and Executive brief, and inside the overlay.
   - In the overlay, it attaches to the overlay's own scroll container, scrolls the embedded report (not Pending), and sits inside the overlay frame clear of the toolbar.
   - It never covers the Technical details switch, the Review decisions bar or the sticky compact header; offset it when they're present.
   - Any page that becomes long gets it automatically.

3. Quality report layout: move "Question for the owner" from the right column to the left column, directly under the history comparison card ("Close match …"), so both columns end at a similar height. Same in the overlay. On phone, keep it after the issues.

4. Tests and docs:
   - Pending: decision on the CRQ line only when made (Approved, Needs work, none, not viewed + decided); no DECISION row.
   - Back to top: hidden at first, visible after one viewport, scrolls to the top, and focus moves to the heading — on each page and in the overlay (scrolling the report, not Pending). No overlap with the bottom-right controls.
   - Report: the card is in the left column.
   Update the user guide and CHANGELOG (no new version). Run the browser tests and `python scripts/check.py --browser --audit`; report counts.

No branches, tags or commits.


git status
git add -A
git commit -m "Pending: decision on the CRQ line when made; Back to top on all long pages and the overlay; balanced report columns"
git push