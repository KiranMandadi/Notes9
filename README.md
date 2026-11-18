0.54.0 polish (CSS only, no rule changes). UI level (browser tests -k pending only).
Review decisions segmented control: make it read clearly as a control, matching the
List | Calendar toggle — track background #E6EBF2 with 3px padding and 10px radius;
options 28px high, 8px radius, 13px text #5B6880, counts in a muted weight; selected
option white with shadow 0 1px 3px rgba(11,27,51,.16), text #0B1B33 bold; hover on
unselected options background rgba(255,255,255,.6); visible focus ring. No layout shift.
Then stop.


python scripts/check.py --browser --audit
git status
git add -A
git status
git commit -m "0.54.0: record the review decision from the Pending list" -m "- Approve / Needs work icons on each row awaiting approval, on the CRQ line; shown on
  hover or focus (green / amber row edge shows the decision at rest); always on touch
- One decision per change, shared with the Review overlay in both directions
- Confirmation coloured by decision (green / amber) with Undo; Clear asks first
- All / Not decided / Decided segmented filter with counts (awaiting approval only)
- Removed the 'last opened' row marker
- Keyboard: arrows, A, N, Enter; Guide, user guide, CHANGELOG and tests updated
- UI only: rule set unchanged"
git push