Answers — go:
1) Stale-task rule ID: CV-13.
2) CV-04: option (b) — scope and type checks stay on every change as today; the
   justification is required only when CC-05's check finds a freeze hit (before exception
   suppression).
3) Agreed: use the period's dates/times in messages, e.g. "Task “X” (Thu 5 Nov 22:00–23:30 ET)
   falls in the restricted period Wed 4 Nov 09:00 – Sun 8 Nov 21:00." Same style for CC-09
   and CV-13.
4) All freeze displays follow CC-05's result (report At a glance Freeze row, verdict-line
   freeze clash, Pending freeze value/tag and calendar ❄):
   - CC-05 Blocker → today's freeze clash display
   - suppressed by exception → today's exception display
   - CC-09 only → neutral text "Window spans a freeze — no work inside", no clash wording,
     no red, no ❄
   - no freeze involvement → nothing
   Keep styles otherwise unchanged; cover these in tests.
5) Run the steps one by one (ruff, crq rules validate, catalogue check, pytest, browser,
   audit), skipping only the baseline. I will run --update-baseline after review.
6) Fine.
Also: treat Cancelled and Rejected changes as not started (as in the measurement).
Report the counts against the agreed numbers, files changed, tests, the new rule set id.
No git.