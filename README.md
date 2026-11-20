git add -A
git status
git commit -m "0.57.0: change awareness periods shown on the window" -m "- calendar.yaml: awareness list (Critical / High) from the events calendar, separate
  from freeze periods; freeze period renamed to its published event name
- Pending: one restriction pill per change (Freeze > Freeze · exception > Critical > High
  awareness) with every overlapping period in its tooltip; Freeze red with a lock icon,
  Critical amber, High violet
- Review At a glance and Calendar show awareness periods
- Review decisions filter shows text and counts only
- Local-time tooltip on window times removed (times are shown in ET)
- Context only: no rule, no score change
- Rule set 0999d7d3 -> 91237364; baseline, docs, CHANGELOG and tests updated"
git push