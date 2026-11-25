OK, that stop was right; continue STEP 1 from where you left off. Reminder: no heredocs,
python -c, python - or stdin redirects into python; use script files under work/ if needed,
and delete them afterwards.

Your three decisions are fine, except CC-09: before finishing, tell me in one line what
CC-09 checks and when it would show next to CC-05. It must not report a restricted period
based on task times. If its only job is to say "tasks run outside the restricted period",
retire it (status: retired, like CV-02/03/08) instead of keeping it.

Then finish the "Not done" list, run the verification, and report: files changed, rule set
old -> new, the live after-comparison against work/cc05_before.json (codes and counts only).
Delete work/cc05_before.json, work/cc05_snapshot.py and work/cc05_new_review.md at the end.