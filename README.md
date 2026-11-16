Diagnosis and measurement only (0.52.1 still open; baseline NOT updated). Read-only: no
code, config, rule or baseline changes.
Constraints unchanged: never read/search/print cr_core/config.py, cr_core/history/config.py
or .env; no Remedy writes; no crq login; no git; no inline Python (-c/stdin/heredoc) —
scripts in a file under work/, deleted after; chat shows codes and counts only — no change
numbers, names or note text.
Scope: Pending (Scheduled For Approval) for the profile groups, plus the 4,483-change live
window scope (Cancelled/Rejected skipped).

Not in scope (confirmed correct, no changes): the open-task scheduled dates rule and the
Exec Summary rule.

1) "No impact" rule (Major, and the Minor variant for impact answers):
   - Does it only look after the phrase for a reason? Show file/function.
   - Simulate accepting a reason in the same sentence or the sentence before, e.g.
     because / as / since / hence / so / therefore / not used / no consumers / shadow mode /
     read-only, or a scoped clause such as "no impact to <X>" alongside a stated possible
     impact ("temporary disruption is possible; no impact to transactions").
   - Majors and Minors cleared / kept / added.

2) LPAR/region/subsystem, scheduler and cycle rules (mainframe):
   - Rule ids and how each decides Major vs "Please confirm" (why the same LPAR check is a
     Major on some changes and Please confirm on others).
   - Hits split by detected platform (ChangeMan package, Control-M scheduler, SPR
     hold/release/job, other mainframe) and by Template+ value.
   - Simulate: Major only when the text shows the change touches that object
     (scheduler/cycle: job, JCL, batch, schedule, cycle words; LPAR: CICS, IMS, Db2
     subsystem, region, LPAR words); Control-M scheduler tickets and SPR hold/release do
     not need an LPAR; otherwise "Please confirm" (0 points). Majors cleared / kept / added.

3) Release-name rule (Minor):
   - Hits by change type: credential/password rotation, index/DDL/data change, patching,
     configuration, application deployment.
   - Simulate applying it only to application deployments/releases (deployment words,
     PCF/Harness/Blue-Green, artifact, build, package promotion). Minors cleared / kept.

4) Vague "etc" rule (Minor):
   - How many hits fall inside the Notes template's own text (e.g. "(Blue/green, Canary,
     etc)", "(LG, CES CAB, HRCAB etc.)")? List the template phrases found, with counts.
   - Simulate ignoring template text (exact template lines, or text inside the template's
     parentheses). Minors cleared / kept.

5) Task links ("View task n"):
   - Confirm n is the Remedy sequence (shared by parallel tasks), giving duplicates such as
     "View task 1" x9. Propose unique labels (e.g. the task's own position, or
     "Step 2 · task 2 of 3") and how the link target is kept.

6) Summary table: item, current hits, cleared, kept, added, recommended handling, one-line
   reasoning. Verdict changes if all recommendations are applied (to Ready,
   Blocked -> Needs work, any worse).

Write work/livecheck_review.txt with 5 examples per item 1-4 (rule id, change id, snippet
<=120 chars, current result, simulated result) for my review only; do not print it in chat.
Propose fixes; then stop.