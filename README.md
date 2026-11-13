Two small fixes on the Pending table. No other changes.

1) Row status pill (Window column, third line)
   It now stretches to the full column width (grey bar). Make it a compact pill sized to its
   text again: display:inline-flex; width:auto (fit-content); align-self:flex-start;
   padding 2px 8px; font-size 11px; font-weight 600; border-radius 999px; same colours as before.
   Keep the 10px space above it. Check every row, including when the Window text wraps.

2) Quality score size
   In the Pending table's Quality column, reduce the score number to 14px, font-weight 600,
   colour #1C2A42 (same as other row text), line-height 1.2. Keep the Ready / Needs work /
   Blocked pill below it, its 4px gap, and the centring unchanged.
   Pending table only — don't change the score on the quality report or anywhere else.

Testing: run only the Pending browser tests that cover the row status pill and the Quality
column; update any test that checks the old score size. Report files changed and pass/fail
counts, then stop.

Standing rules: no git, no inline Python, don't read cr_core/config.py, cr_core/history/config.py
or .env, don't run --update-baseline. Codes and counts only.

git status
git diff --stat
git add -A
git status
git commit -m "Pending: clear loading and status messages above the table" -m "- One status pill on the line above the table (left), Review decisions stays right
- States: loading a stage, refreshing, slow (amber after 10 s), failed (with Retry), updated (fades after ~4 s)
- Refresh button shows Refreshing..., table dims to 85% while rows are replaced
- Progress cursor while any load, refresh or retry is running
- Cancel aborts the request; cancelling a stage load un-ticks it; newer loads supersede older ones
- Report-opening messages (slow / couldn't open) use the same status pill
- Respects reduced-motion; old in-table and scattered messages removed
- Row status pill: compact again, with 10 px space above it on the Window column's third line
- Quality score in the Pending table reduced to 14 px
- Tests, user guide and CHANGELOG updated"
git push