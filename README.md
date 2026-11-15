Window check, measurement follow-up. Same read-only constraints. Keep
work/windows_spotcheck.txt for now; everything else under work/ deleted after.
1) Reconcile: the summary said 120 better / 40 worse, the table shows 115+60 better,
   30+10 worse. Which is right?
2) Re-run with tasks entirely outside the change window excluded (as CC-05 does). Give the
   new Major / cleared / fallback counts per Type of Window and the verdict table.
3) Fallback (no usable implementation task): split by status group and by "has no tasks
   at all" vs "has tasks but none named implementation". For the second group, the 25
   most common task-name patterns (normalised: lowercase, digits and change ids removed),
   with counts. Names only, no change ids.
4) Majors: how far outside the allowed hours: total minutes outside per change, bucketed
   <=15, 16-30, 31-60, 61-180, >180. Same split for Authorized vs Specialized.
5) "Crosses midnight" Majors (Authorized): how many fail because they end after 07:00 or
   start before 20:30/14:00, versus failing for any other reason. Any failing task wholly
   inside 20:30-07:00 is a bug: count them and explain.
Then stop.