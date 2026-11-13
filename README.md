git status
git diff --stat
git add -A
git status
git commit -m "Pending: clear loading and status messages above the table" -m "- One status pill on the line above the table (left), Review decisions stays right
- States: loading a stage, refreshing, slow (amber after 10 s), failed (with Retry), updated (fades after ~4 s)
- Refresh button shows Refreshing..., table dims to 85% while rows are replaced
- Progress cursor while any load, refresh or retry is running
- Cancel aborts the request; cancelling a stage load un-ticks it; newer loads supersede older ones
- Respects reduced-motion; old in-table and scattered messages removed
- Row status pill: 6 px space above it on the Window column's third line
- Tests and CHANGELOG updated"
git push