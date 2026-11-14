Re-run the same READ-ONLY measurement with these changes (temporary helper under work/,
delete it afterwards; no inline Python; no rule/config/test changes; no git):

A) Reference tasks = name contains "implementation" or "certification" (case-insensitive),
   EXCLUDING names containing "rollback" or "backout", and names starting with
   "pre implementation", "pre-implementation", "post implementation", "post-implementation".
   Status not Cancelled/Canceled/Bypassed (Closed counts).
B) Use only reference tasks with VALID dates (both present and end > start). Undated or
   inverted reference tasks are ignored. Fall back to the change window ONLY when no
   reference task has valid dates.

Report the same table (history / live all stages / Scheduled For Approval), plus:
1) fallback split: no reference task vs. no reference task with valid dates
2) how many changes have BOTH dated and undated reference tasks (now task-based)
3) RISK CHECK: changes that become Advisory or no-finding while a NON-reference task in this
   list overlaps a freeze: names containing "changeman", "redbutton", "load balancing",
   "poolmember", "auto deployment", "deploy", "tso id upgrade", "cutover", "release".
   Count, and which of those names.
4) NEW Blockers (task in freeze, change window not): status breakdown (Planning In Progress /
   Scheduled For Approval / Scheduled), and how many have the task ENTIRELY outside the
   change window.
5) Write the change numbers of the new Blockers and the risk-check changes to
   work/cc05_review.txt (one per line, with the reason code) so I can check them myself in
   Remedy. Do NOT print them in the chat. Tell me the file path.

Codes and counts only in the reply.