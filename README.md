Pending window pills: "Today" uses the same font size, weight, height and padding as
"Tomorrow" (and the other date pills). Keep its current background colour unchanged.
Browser test -k pending only. Then stop.

python scripts/check.py --update-baseline
python scripts/check.py --browser --audit
git status
git add -A
git status
git commit -m "0.55.0: 'How this was assessed' explanation for every finding" -m "- Each finding carries what was checked, what was found, why this severity, what would
  change it and when it counts, set by the rule that raised it
- 'How this was assessed' link on every issue and advisory, always visible; opens the
  rule panel with the explanation above How to meet it and the source
- Specific severity reasons for CV-15, CV-18, CC-05/06/09/10/12, CV-13, CV-14, MF-01,
  INF-05 and the Exec Summary rules; plain fixed-severity wording for the rest
- Change Assessment questions shown as chips (core bold, gaps amber)
- Same panel in the Pending overlay; Guide FAQ, user guide, CHANGELOG and tests updated
- Rule set 57e6af7f -> <new id>; baseline updated"
git push