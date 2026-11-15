Window check: measurement only. Read-only. No code, config, rule-pack, baseline or
history-schema changes. Do not read cr_core/config.py, cr_core/history/config.py or .env.
No writes to Remedy. No git. Scripts in a file under work/, no inline Python; delete
when done. In chat: codes and counts only, no change numbers, names or summaries.

Scope: the profile's support groups, Scheduled Start 2026-08-17 to 2026-12-15, all
classes and statuses (the same ~4,867 changes as the discovery). Live read.

Proposed check, to simulate in the helper only:
A) Tasks: implementation tasks only — name contains "implementation" (case-insensitive),
   excluding names with rollback/roll back/backout/back out and names starting with
   pre-implementation/post-implementation. Certification tasks are NOT checked. Same task
   status logic as CC-05 (not-started changes: open tasks; started/done: open + Closed
   with Status Reason not Cancelled; ignore Cancelled/Canceled/Bypassed). Only tasks with
   valid dates (end > start). Times converted to America/New_York.
B) Allowed hours:
   - Type of Window Authorized or blank: Mon-Fri 20:30 -> 07:00 next day; Sat-Sun
     14:00 -> 07:00 next day (i.e. restricted Mon-Fri 07:00-20:30, Sat-Sun 07:00-14:00).
   - Specialized: read the window row live from SCHW:CHG:TemplatizeFields (Field Name =
     Specialized Windows, Contents = Platform, Contents1 = window, Status Active), slots
     <Day>_ST1/ET1 and ST2/ET2 (Sunday first). Join slots across midnight (23:59:59 +
     00:00). One read per distinct window, no caching between runs.
   - A task passes only if every minute from start to end is inside allowed hours.
C) Exception: any Work Detail of type Restriction Approval Notes, Restriction Exception or
   Windows Exception clears a failure (count it as "cleared").
D) No usable implementation task: compare the change window instead, advisory only.
E) Completeness: Specialized with no window chosen; Type of Window blank on a change past
   Draft.

Report:
1) Per Type of Window (Authorized / Specialized / blank): changes; with usable impl
   tasks; fallback to change window; pass; fail; fail cleared by exception; Major
   (fail, not cleared); fallback advisories.
2) Major and cleared, split by class (Normal/Expedited/Standard/Emergency/Other) and
   status group (not started / in progress / closed).
3) Specialized: Major count per Platform x window; windows not found or Inactive
   ("not checked") with counts.
4) Failure shape for Majors: starts in restricted hours / ends in restricted hours /
   whole task restricted / day not allowed / crosses midnight.
5) Completeness counts for E.
6) Old rules on the same changes: current hits of MF-05, CC-08, the weekend max_risk
   check and any other rule reading mf-online / mf-batch-critical / business-hours /
   weekend periods (rule id, severity, count). Then the overlap: changes flagged by old
   rules only, new check only, both.
7) Score impact: changes whose verdict would change (Ready->Needs work, Needs work->Ready,
   any ->Blocked) if old rules are retired and the new check is Major (-20).
8) Spot-check list: write work/windows_spotcheck.txt with 15 changes (5 pass, 5 Major,
   5 cleared; mix Authorized and Specialized) showing change id, type/platform/window,
   impl task times (ET) and the result. Do NOT print it in chat; I will review it in
   Remedy and then you delete it.
Then stop.