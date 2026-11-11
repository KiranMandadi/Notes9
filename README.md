ORR naming. Same standing rules; no git operations unless I ask. UI only.
1. Pending ORR filter popover: title "Operational Risk Rating (ORR)" (same heading style). Chip label stays "ORR …".
2. ORR chip: title tooltip "Operational Risk Rating".
3. Table column header ORR: same tooltip "Operational Risk Rating".
Tests (UI tier): popover title text; tooltips present. Run ruff and browser tests -k "pending or filter". One CHANGELOG line.
No branches, tags or commits.


git status
git add -A
git commit -m "Pending: View by replaced by Risk filters; fixed ORR/Risk Level defaults; pill in results row; Show only <name>; approver clear button"
git push