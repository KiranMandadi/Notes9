READ-ONLY task: inventory EVERY rule and setting related to implementation timing and windows.
Change nothing.

Include anything that checks or uses WHEN a change is implemented, for example:
- Freeze / blackout / moratorium windows and freeze exceptions
- Platform-specific windows: mainframe windows, distributed/open-systems windows, network,
  database, or any per-platform / per-product / per-support-group window
- Allowed days and hours (weekday/weekend, overnight, business hours, market/trading hours,
  batch windows, start/end cut-offs)
- Month-end, quarter-end, year-end, holiday or special-event restrictions
- Lead time: how far ahead a change must be raised, submitted or approved (per class,
  e.g. Normal / Expedited / Emergency / Standard, and per risk level)
- Approval timing: approval required before start, CAB/meeting cut-offs
- Window length / duration limits, multi-day changes, start in the past, already started,
  end before start, missing dates
- Overlaps/conflicts with other changes or outages, if any
- How "Today", "Tomorrow", "started" and "Freeze · exception" are worked out on Pending
- Any timezone handling (ET vs UTC vs local) used by these checks

Look everywhere these can live: profiles/enterprise/config/*.yaml (all files), the rule
packs, cr_core/quality/*, any other cr_core module that reads dates/times, docs/
(rules, decisions, configuration), and tests that pin this behaviour.

Reply with:
A) ONE table, one row per rule or setting:
| Rule ID | Name | Severity (Blocker/Major/Minor/Advisory/none) | Exact trigger (condition,
  thresholds, days/hours, timezone, which Remedy fields/dates) | Applies to (class, risk
  level, platform/product/group, status, history replay) | Exceptions / overrides |
  Config source (file + key) or "hard-coded in <file>" | Message shown |
B) Every configured window/calendar exactly as stored (name, platform/scope, days, start–end
   times, timezone, date ranges).
C) Platform detection: how the code decides a change is mainframe vs other (which field,
   values, mapping file).
D) Gaps or risks: inconsistent, duplicated, hard-coded, or timezone-unsafe logic, and any
   timing rule mentioned in docs but not implemented (or the reverse).

Rules: don't read cr_core/config.py, cr_core/history/config.py or .env. No git, no inline
Python, no tests to run, no file changes. Rule IDs, conditions and config values are fine to
show; no change numbers or people's names.