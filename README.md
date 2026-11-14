git status
git diff --stat
git add -A
git status
git commit -m "Pending: more visible loading and refresh status" -m "- Progress bar (3 px) on the table's top edge while loading/refreshing; amber when slow
- Status shown as a message (tinted fill, left accent bar, 8 px radius), distinct from filter chips
- Slow state shows elapsed seconds; Refresh icon spins while refreshing
- Table dims to 70% during refresh
- No flicker: shown only after 300 ms, kept at least 600 ms
- Reduced-motion respected; Pending browser tests updated"
git push