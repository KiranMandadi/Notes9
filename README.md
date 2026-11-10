Filter popover polish. Same standing rules; no git operations unless I ask. UI only; rule set id unchanged — confirm it.
1. Keep "Only" on every multi-select (Class, Status, Organisation, Group rows and Group organisation headings).
2. "Only" visibility: show it only on mouse hover of its row, or when the row has :focus-visible (keyboard navigation). Never visible by default. When a popover is opened by mouse click, put focus on the popover container (not the first row), so nothing shows "Only" until hovered. Opening by keyboard may focus the first row as today.
3. Status popover: on hover/focus-visible of an unloaded stage row, hide "Loads when selected" and show "Only" in its place (no overlap). On loaded rows, "Only" sits before the count as elsewhere.
4. Class popover footer: one line, "N of M selected · Standard not included by default" when Standard is unticked; otherwise just "N of M selected".
Tests: opening each popover by click shows no "Only"; hovering a row shows it; Tab into the list shows it on the focused row. Update screenshots; CHANGELOG (no new version). Run the browser tests with pytest; report counts.
No branches, tags or commits.

git status
git add -A
git commit -m "Pending filters: Select all/Clear/Only, zero-count values tucked away, honest labels, Group scoped by Organisation"
git push