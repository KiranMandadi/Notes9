Read-only research on CC-10/CC-12 "no usable implementation task". No code, rule, config or
baseline changes. No git.

Policy (confirmed): validation and certification tasks are never implementation tasks for the
window check and may run in any window. A task whose name contains both "Implementation" and
"Validation"/"Certification" is a validation/certification task.

1) Explain what makes an implementation task "usable" today: accepted statuses, how
   implementation vs validation/certification is decided (name, type, field, and which wins
   when both words appear), any duration cap or other guard. Quote config keys/values, not code.
2) On live data (same scope as the audit), codes and counts only:
   - changes where CC-12 fires with "no usable implementation task";
   - of those, how many have an open implementation task (per the policy above) with both
     scheduled start and end; for each such task the rejection reason (status value,
     duration cap, other);
   - counts of status values on open implementation tasks (Staged, Assigned, Pending,
     Scheduled, Work in Progress, ...);
   - how many tasks are currently classed as implementation but are validation/certification
     by the policy above (and the reverse);
   - if fixed per policy: how many CC-12 would pass, become CC-10 (Major), or stay CC-12.
3) Write work/cc12_review.md: change number, task step, status, scheduled start/end, class
   today vs class by policy, rejection reason. No names. I will delete it.
Do not read cr_core/config.py, cr_core/history/config.py or .env. Never delete anything under
work/history/. No heredocs (not even empty ones), python -c, python - or stdin redirects.
Then stop and report.