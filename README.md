Pending polish. Same standing rules; no git operations unless I ask. UI only; rule set id unchanged.
1. Hidden-changes pill: neutral style — background #EEF1F6, text #44516A, no border; keep the "Show all M" link teal #0E7C74 underlined. Same size and position (results row, after "Showing N of M").
2. Restore the Review decisions bar ("Review decisions · Decided N of M · Copy Decisions · Clear") to its previous place: above the table card, right-aligned, outside the card, same style and spacing as before this round. The table's results row holds only: sorted-by text, "Showing N of M", the pill (left) and the search box (right) on one line.
3. Risk Level chip label: show the value without repeating the name — "Risk Level 5, 4, 3" (not "Risk Level Risk Level 5, 4, 3"); "Risk Level All" when all are ticked.
Tests (UI tier): pill colours; decisions bar above the table card on the right and not inside it; search on the same line as the results text; Risk Level chip label. Run ruff and browser tests -k "pending or filter". One CHANGELOG line.
No branches, tags or commits.


git status
git add -A
git commit -m "Pending: View by replaced by Risk filters; fixed ORR/Risk Level defaults; pill in results row; Show only <name>; approver clear button"
git push