Guide polish, last two (Pending miniature). UI only.
1) Filter rows: label column fixed width; chips wrap within the chip column, so the wrapped
   "Approver A. Approver" chip starts under "Status Scheduled For Approval", not under "SCOPE".
2) Status message: the left accent is a straight 3px bar inside the tinted fill (e.g.
   box-shadow: inset 3px 0 0 <green> or a ::before), not a border that curves with the radius.
   Match the real Pending page's message exactly.
Run the Guide browser tests and ruff only. Report files and counts; then stop. No git.

git status
git diff --stat
git add -A
git status
git commit -m "0.51.0: Guide page" -m "- New Guide tab (flag CHANGELENS_GUIDE, on by default): parts of the report, scoring
  simulator (weights and thresholds from config), the Pending page, FAQ, glossary, data handling
- Report and Pending miniatures match the real pages: heading-and-row cards, filter chips with
  values, green status message; numbered hotspots linked to the parts list, with a divider
- Static page: no Remedy calls; neutral professional copy
- crq doctor shows Guide on/off; docs, SECURITY.md, CHANGELOG and tests updated
- Rule set id unchanged"
git push