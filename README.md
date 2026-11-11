Correction to item 2: do NOT move the Review decisions bar. Restore "Review decisions · Decided N of M · Copy Decisions" to its previous place — above the table, right-aligned, same style and spacing as before this task. Only the hidden-changes pill lives in the results row (after "Showing N of M"); the line above the table now holds just the decisions bar on the right. Update the affected browser test(s) to assert the bar is above the table on the right. UI tier: ruff + browser tests -k "pending or filter". No git operations.


git status
git add -A
git commit -m "Pending: View by replaced by Risk filters; fixed ORR/Risk Level defaults; pill in results row; Show only <name>; approver clear button"
git push