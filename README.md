Window check: build (0.52.0). Replace the placeholder window rules with a window check
based on Remedy's Type of Window / Platform / Specialized Windows and the authorized
window. Goal: a Major only where the data proves it; anything uncertain is advisory or
not checked.

CONSTRAINTS (unchanged): never read/search/print cr_core/config.py,
cr_core/history/config.py or .env; no Remedy writes (REMEDY_ALLOW_CREATE stays off); never
run crq login; no git; no inline Python (-c/stdin/heredoc) — scripts in a file under work/,
deleted after; do NOT run --update-baseline (I run it); history.db schema unchanged and no
people stored; chat shows codes, counts and normalised names only, no change numbers,
names or summaries.

1) RETIRE: MF-05 (online day / batch critical path), CC-07 (weekend risk limit), CC-08
   (start in weekday business hours), and the calendar.yaml periods mf-online,
   mf-batch-critical, business-hours and weekend max_risk. Remove from rule packs and
   config; IDs not reused; list them as retired in CHANGELOG and the rules docs. Freeze
   periods and CC-05/CC-09/CV-13 are unchanged.

2) DATA (read-only, live):
   - remedy_field_map.yaml: add Type of Window, Platform, Specialized Windows (ids from
     the discovery). Read them with the change. History replay: fields absent -> the new
     rules are "not applicable" (no findings); history schema unchanged.
   - Window hours: read the matching row from SCHW:CHG:TemplatizeFields (Field Name =
     Specialized Windows, Contents = Platform, Contents1 = window, Status = Active) with
     <Day>_ST1/ET1 and ST2/ET2 (Sunday first). One read per distinct window per request
     (in-request memo only, no cache across requests). Blank day = no hours; 23:59:59
     joins to 00:00 next day; end exclusive. If more than one Active row, or the read
     fails/times out -> "not checked" (CC-12), never a Major.

3) CONFIG (calendar.yaml, new window_check block):
   - timezone: America/New_York (task times are UTC epoch; convert with DST).
   - authorized: Mon-Fri 20:30 -> 07:00 next day; Sat-Sun 14:00 -> 07:00 next day.
   - holidays treated as weekend days (14:00 -> 07:00): US market holidays 2026 and 2027
     as a dated list (2026-01-01, 01-19, 02-16, 04-03, 05-25, 06-19, 07-03, 09-07, 11-26,
     12-25; 2027-01-01, 01-18, 02-15, 03-26, 05-31, 06-18, 07-05, 09-06, 11-25, 12-24),
     with a comment to confirm yearly.
   - start_grace_minutes: 30 (restricted minutes only in the 30 min before an allowed
     block starts -> advisory, not Major).
   - task_include: name contains "implementation" (case-insensitive); task_exclude: names
     containing certification, rollback, roll back, backout, back out, or starting with
     pre-implementation / post-implementation.
   - copy_tolerance_minutes: 1; max_task_hours: 24.
   - exception_work_detail_types: Restriction Approval Notes, Restriction Exception,
     Windows Exception.

4) RULES
   CC-10 (Major, -20) "Implementation task outside its allowed window". Evaluate per change:
   a) Skip entirely: change status Cancelled or Rejected; history replay without fields.
   b) Tasks: task_include/exclude; same status logic as CC-05 (not-started changes: open
      tasks; started/done: open + Closed with Status Reason not Cancelled; ignore
      Cancelled/Canceled/Bypassed); valid dates (end > start); exclude stale tasks
      (entirely outside the change window; CV-13 reports them); exclude tasks already
      flagged by CC-05 for a freeze.
   c) Allowed hours = authorized hours (with holidays) PLUS, when Type of Window =
      Specialized and the window row is found, that window's slots. A task passes only
      if every minute start..end is allowed.
   d) A failing task gives a Major ONLY if ALL hold: class is not Emergency; Type of
      Window is Authorized or Specialized (not blank); task start/end are not within
      copy_tolerance of the change's scheduled start/end; task <= max_task_hours;
      restricted minutes are not all inside the start grace; no Work Detail of the
      exception types; no Work Detail of any other type whose notes contain "exception"
      (case-insensitive).
      If it fails but any condition above is not met -> CC-12 advisory with the specific
      reason. If an exception Work Detail exists -> no finding; report shows
      "Outside the window; window exception recorded" as an info line.
   e) No usable implementation task -> compare the change window the same way;
      advisory only (CC-12), never Major.
   f) One CC-10 finding per change; message lists up to 3 tasks with ET times, the
      allowed hours applied (e.g. "Authorized: Mon-Fri 20:30-07:00" or "ChangeMan
      Packages - Affecting Batch Processing Only: Mon-Fri 16:30-23:30") and how to fix
      (reschedule, or record a Windows Exception in Work Detail).
   CC-11 (Minor, -5) "Window type not set": change past Draft with Type of Window blank,
      or Specialized with no Platform/window chosen. Not for Cancelled/Rejected.
   CC-12 (Advisory, 0) "Window could not be confirmed": the advisory cases above, each
      with a plain reason (Emergency change; Type of Window not set; task copies the
      change window; task longer than 24 h; starts within 30 min before the window;
      possible exception in notes - record it as Windows Exception; no usable
      implementation task; window hours unavailable).
   Neutral wording, no "your".

5) TESTS (tests/test_rules.py and friends), each dimension: authorized weekday/weekend/
   holiday; crossing midnight; Friday->Saturday; DST 2026-11-01 and 2026-03-08; specialized
   slots incl. 23:59:59 join, blank day, two slots, 24x7; authorized OR specialized;
   start grace; copy-of-change-window; >24h; Emergency; blank type; Cancelled/Rejected
   skipped; stale excluded; CC-05 overlap excluded; exception types clear; "exception"
   in other notes -> advisory; no usable task -> advisory; window read failure / duplicate
   Active rows -> not checked; certification/rollback/pre-/post- tasks ignored; history
   replay without fields -> no findings. Existing tests stay green (do not weaken any).

6) DOCS: rules docs, configuration.md (window_check), user-guide (short section),
   architecture (live window read), SECURITY.md (read-only, no cache across requests),
   CHANGELOG 0.52.0, pyproject version 0.52.0. Guide page glossary: add "Specialized
   window" one line.

7) VERIFY: ruff; full test suite; scripts/check.py --browser --audit must show 0
   mismatches apart from the expected rule-set/baseline change (report the new rule set
   id). Do not update the baseline.

8) MEASURE WITH THE BUILT CODE (read-only, same 4,881 changes as the discovery): per Type
   of Window: pass / exception cleared / CC-10 / CC-11 / CC-12 by reason / not checked /
   skipped; CC-10 by class, status group, platform x window; verdict changes vs the
   current release (Blocked->Needs work etc.). Then replace work/windows_spotcheck.txt
   with 40 changes from the BUILT rule: 25 CC-10 stratified (Authorized short/long/
   midnight; Specialized per platform; Draft and Closed) and 15 others (pass, cleared,
   CC-11, CC-12 per reason). Each row: change id, class, status, type/platform/window,
   checked tasks with ET times, allowed hours, result and reason. Do not print it in chat.
Report files changed, test counts, audit result and the measurement; then stop.