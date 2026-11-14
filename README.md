Task: CC-05 freeze check based on implementation/certification tasks + new CV-11
(stale task). Release 0.49.0. Measured and agreed — implement exactly.

=== STEP 1: PLAN ONLY, then STOP ===
Reply with: files to change, where CC-05/CV-04/CV-09/CV-10 live, how tasks reach the rules
(live and history replay), how advisory findings are emitted today (CV-02/CV-03 pattern),
and confirm the new rule IDs below are unused. Wait for my "go".

=== CONFIG (no hard-coding; put in the calendar/core config with comments) ===
reference_tasks:
  name_contains_any: ["implementation", "certification"]          # case-insensitive
  exclude_name_contains_any: ["rollback", "roll back", "roll-back",
                              "backout", "back out", "back-out"]
  exclude_name_starts_with: ["pre implementation", "pre-implementation",
                             "post implementation", "post-implementation"]
  ignored_statuses: ["Cancelled", "Canceled", "Bypassed"]
  cancelled_status_reasons: ["Cancelled", "Canceled"]
  not_started_change_statuses: [Draft, Request For Authorization, Request For Change,
    Planning In Progress, Scheduled For Review, Scheduled For Approval, Scheduled]
Name matching: lower-case, collapse whitespace, then apply the lists.

=== DATA ===
- Live: add task Status Reason (TMS:Task StatusReasonSelection) to remedy_field_map.yaml
  task fields; read it with the existing task query (no extra Remedy calls).
- History replay: pass the stored tasks.status_reason to the rules.
- Never log or print task contents beyond what reports already show.

=== REFERENCE TASK SELECTION (per change) ===
1) Name matches the config lists.
2) Ignore ignored_statuses.
3) Change not started → only tasks that are NOT Closed.
   Change started/done (Implementation In Progress, Completed, Closed, or anything else) →
   open tasks + Closed tasks whose Status Reason is not in cancelled_status_reasons.
4) Valid dates only: scheduled start and end present and end > start.
5) Stale = valid task ENTIRELY outside the change window (ends at/before window start, or
   starts at/after window end). Stale tasks are excluded from CC-05 and reported by CV-11.
   (If the change has no window, nothing is stale.)

=== CC-05 (Blocker) — freeze ===
- If ≥1 usable reference task (valid, not stale): Blocker when any of them strictly overlaps
  a freeze period (same ET boundary logic and exception Work Detail suppression as today).
  Message names the task(s): "Task “{task name}” ({start}–{end} ET) falls in the freeze
  {freeze name}." Several tasks → list them.
- If none usable → fall back to the change window exactly as today.
- Exceptions (Restriction Approval Notes / Restriction Exception) still suppress, unchanged.

=== CC-09 (Advisory, 0 points) — window spans a freeze, no work inside ===
When CC-05 used tasks, found no task in a freeze, but the change window overlaps a freeze:
"The change window spans the freeze {freeze name}, but no implementation or certification
task is scheduled inside it." (Use CC-09 only if unused; otherwise propose an ID.)

=== CV-11 (Major) — task outside the change window ===
For each stale reference task (any change status, exceptions don't suppress it):
"Task “{task name}” ({start}–{end} ET) is entirely outside the change window
({window start}–{window end} ET) — update the task dates."
If that task overlaps a freeze, append: " It currently falls inside the freeze {freeze name}."
One finding per change listing all stale tasks.

=== RELATED RULES ===
- CV-04 (freeze fields incomplete): apply only when CC-05 would fire as a Blocker-level freeze
  hit (before suppression), not when only CC-09 applies. Report the count change.
- CV-09 / CV-10 unchanged. CV-10 must not double-report a task already reported by CV-11
  (skip CV-10 for that task).
- Pending page "Freeze" tag: follow the CC-05 result — Blocker → "Freeze", suppressed by an
  exception → "Freeze · exception", CC-09 only → no freeze tag. Styles unchanged.

=== MEASURE AGAINST THE AGREED NUMBERS ===
Run the history audit and a live Pending read and report counts:
expected ≈ history: CC-05 Blocker 13, CC-09 11, CV-11 in 16 changes, 0 new Blockers vs today;
live (all stages): CC-05 28, CC-09 2, CV-11 in 75 changes (11 stale-in-freeze), 0 new
Blockers. Explain any difference.
- scripts/check.py --browser --audit: report mismatches (must be 0 apart from the expected
  rule-set change). Do NOT run --update-baseline — I will.

=== TESTS (tiered) ===
Unit tests for: name include/exclude (incl. prefixes, "rollback plan: certification",
"pre implementation monitoring"), status/status-reason filtering for not-started vs started
changes, invalid/inverted dates, stale detection (entirely vs partly outside), task-in-freeze
Blocker, window-only Advisory, fallback paths (no reference task / none usable / only stale),
exception suppression, CV-04 gating, CV-10 not duplicating CV-11, Pending tag mapping, ET/DST
boundaries. Run test_rules.py, test_contracts.py, the Pending browser tests for the tag, and
ruff. Not the full gate.

=== RELEASE ===
Version 0.49.0. CHANGELOG + docs (rules reference for CC-05, CC-09, CV-11; config keys).
Rule set id will change — tell me the new id.

=== STANDING RULES ===
Never read/search/print cr_core/config.py, cr_core/history/config.py or .env. No git.
No inline Python (no -c, no stdin). Don't run --update-baseline. Never run crq login.
Codes and counts only in replies. Report files changed and counts, then stop.