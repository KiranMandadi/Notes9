Pending: active filter chip style → teal outline. Same standing rules; no git operations unless I ask. UI only.
Replace the teal-filled active-chip style with: background #FFFFFF, border 1.5px #0E7C74, filter name #44516A, value #0B5F59 (700), "×" #0B5F59. Same rule as now: any filter that narrows the list, default or user choice. Inactive chips unchanged (white, 1px #CFD7E3). Applies in both views and to the Approver chip. Keep chip height unchanged (no layout shift from the thicker border).
Tests (UI tier): active chips use the teal outline; inactive stay as before; chip heights equal. Run ruff and browser tests -k "pending or filter". One CHANGELOG line.
No branches, tags or commits.


git status
git add -A
git commit -m "Pending: Refresh progress feedback; highlight narrowing filters; Status limited to Planning In Progress and Scheduled For Approval"
git push