Pending: active filter chip colour → navy tint. Same standing rules; no git operations unless I ask. UI only.
Replace the teal active-chip style with: background #E9EEF6, border 1px #9FB0CC, filter name #44516A, value #0B1B33 (600), "×" #0B1B33. Same rule as now: any filter that narrows the list, default or user choice. Inactive chips unchanged (white). Applies in both views and to the Approver chip. Keep teal for links, Open buttons and "Show all".
Tests (UI tier): active chips use the navy tint; inactive stay white. Run ruff and browser tests -k "pending or filter". One CHANGELOG line.
No branches, tags or commits.


git status
git add -A
git commit -m "Pending: Refresh progress feedback; highlight narrowing filters; Status limited to Planning In Progress and Scheduled For Approval"
git push