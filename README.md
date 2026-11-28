At a glance Window row: keep the duration and the "Longer than 8 h" pill together on one
line (no wrap inside "4 d 3 h 30 min"); if space runs out, wrap the whole duration+pill to
the next line. Saved reports the same. UI only.


git add -A
git status
git commit -m "0.63.1: At a glance Window row keeps the duration on one line" -m "- The window duration and its 'Longer than 8 h' pill stay together; the pair wraps as one
  when space runs out (Console and saved reports)
- UI only; rule set 41275f9f unchanged"
git push