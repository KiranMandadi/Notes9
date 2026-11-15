Window check, measurement round 3: robustness. Same read-only constraints; no
code/config/rule/baseline/history changes; no Remedy writes; no git; scripts in a file
under work/, deleted after; chat shows codes, counts and normalised task names only.
Same 4,881 changes. Baseline = round 2 (stale tasks excluded).

Goal: a Major only where the data proves it. For every dimension below report how many
of the current Majors it would remove or change, and any NEW Majors it would add.

1) Task selection. Alternative rule: check every usable task EXCEPT names (case-insens.)
   containing certification, certify, validation, validate, verification, verify,
   monitoring, monitor, rollback, roll back, backout, back out, or starting with pre-/
   post-. Side-by-side table with round 2 (per Type of Window: pass / cleared / Major /
   fallback / advisory) and verdict table. Top 25 normalised task names behind Majors
   under each rule, with counts. Flag names that look like checks/admin (e.g. "manual
   check", "jira status update", "go forward") and their Major counts.
2) Task dates copied from the change: Majors where the failing task's start AND end equal
   the change's scheduled start/end (to the minute), or within 1 minute.
3) Long tasks: Majors where the failing task lasts >12h, >24h, >72h (counts).
4) Change status: Majors and fallbacks split by Cancelled, Rejected, Draft, other
   not-started, in progress, Completed, Closed. Also explain the 1,125 "implementation
   tasks, none usable" by status and reason (all Cancelled/Bypassed, Status Reason
   Cancelled, invalid dates, stale).
5) Class: Majors by Normal / Expedited / Standard / Emergency / Latent / Other.
6) Type of Window blank: Majors by class and by Submit date year/quarter; how many blank
   changes are Standard (template) changes.
7) Specialized vs authorized: of the Specialized Majors, how many would PASS if the
   authorized hours were also allowed (by platform). And of Authorized/blank passes,
   none affected (confirm).
8) Window table integrity, for the windows in use: duplicate Active rows for the same
   Platform+window (and whether their slots differ); same window name under two
   platforms; days with blank slots vs 00:00-00:00 vs 00:00-23:59:59 (how each is
   stored and how you interpreted it); any slot with start = end.
9) Time zone / DST: confirm task times are epoch UTC converted to America/New_York;
   Majors on 2026-11-01 and 2026-03-08 (and +/-1 day); Majors that would flip if the
   conversion were off by one hour (+/-60 min), as a sensitivity count.
10) Exception evidence: for current Majors, count those that have (a) any Work Detail at
    all, (b) Work Detail of other types whose notes mention exception / outside window /
    approved / HPCAB / waiver (case-insens.; count only, no text), (c) any approval
    records beyond normal (if readable), (d) Timing Reason filled. Report counts per
    signal.
11) Production vs non-production: find the change field(s) that mark environment
    (e.g. Production/Non-production, environment, CI class); Majors split by it. If no
    such field exists, say so.
12) Holidays: Majors whose failing task falls on a US market holiday in the range
    (Labor Day 2026-09-07, Thanksgiving 2026-11-26, plus 2026-11-27).
13) Freeze overlap: Majors that also have a CC-05 Blocker/Major on the same task.
14) Stale: confirm 0 Majors come from tasks entirely outside the change window.
15) 16-30 minute cluster (and all Majors <=60 min): pattern of start/end times (e.g.
    starts 20:00, ends 07:30) with counts.
16) Summary table: each dimension, Majors removed, Majors added, recommended handling
    (exclude / advisory / keep Major), with one-line reasoning.
17) Spot-check: replace work/windows_spotcheck.txt with 40 changes under the alternative
    rule: 25 Majors stratified (Authorized, Specialized per platform, blank, short/long
    overrun, crosses midnight) and 15 passes/cleared. Show change id, class, status,
    type/platform/window, each checked task name + start/end ET, allowed hours applied,
    and the reason. Do not print it in chat.
Then stop.