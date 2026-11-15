Guide polish: parts lists in sections 01 and 03 (UI only).
1) Each row: padding 12px 0, border-bottom 1px solid #E6EBF2; no border on the last row.
   Row height consistent whether open or closed.
2) Active row: remove the outlined box. Full-width row background #F1F8F6 (no border,
   no radius beyond 6px), number filled navy as now, description below the title inside
   the same row. Hover on other rows: background #F7F9FC.
3) Same component for both lists.
Check at 100% and 110%. Run the Guide browser tests and ruff only. Report files and counts;
then stop. No git.


git add -A
git status
git commit -m "Guide: row dividers in parts lists"
git push