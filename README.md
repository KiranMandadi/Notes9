ChangeLens 0.57.0 — change awareness periods on the window (context only, no rule, no score change)

Ground rules (all still in force):
- Never read, search or print cr_core/config.py, cr_core/history/config.py or .env.
- Never delete anything under work/history/. history.db is never committed.
- No git operations. No crq login. No Remedy writes. REMEDY_ALLOW_CREATE stays off.
- Do not run --update-baseline (I run it).
- Codes and counts only in chat; no change numbers, names or submitters printed.
- Any heredoc, python -c or python - is a stop condition: ask instead.
- No passwords or tokens printed, logged or stored.

1) calendar.yaml: awareness list
   Add an "awareness" list to profiles/enterprise/config/calendar.yaml, separate from the
   freeze periods. Each entry has a name, a level (critical | high), and start and end in ET.
   Seed it with:
     - November Production Instability      critical  2026-11-17 13:00 -> 2026-11-25 09:00
     - Thanksgiving Restriction             high      2026-11-25 09:00 -> 2026-11-30 09:00
     - ANEx Rollout - Employee Access       high      2026-12-02 09:00 -> 2026-12-06 09:00
     - Year End Processing 2026             critical  2026-12-18 09:00 -> 2027-01-05 09:00
     - ANEx Rollout - Retail Access Begins  high      2027-01-06 09:00 -> 2027-01-10 09:00
     - ANEx Rollout - Advisor Access Begins high      2027-01-13 09:00 -> 2027-01-17 09:00
   Validate on load: level must be critical or high, end after start; a bad entry is a
   clear config error naming the entry, not a crash.

2) Overlap logic
   A change is "in" an awareness period when its scheduled window (start -> end) overlaps the
   period. Compare in ET and handle DST correctly. Touching at an exact boundary does not
   count (a change ending at 09:00 does not overlap a period starting at 09:00).
   This is context only: no rule code, no finding, no score effect, nothing in the
   Ready/Blocked logic.

3) Pending: awareness pill in the Window column
   One pill per change, showing the highest level that overlaps (critical over high):
     "Critical awareness" text #8A4B08 on #FDF0DC; "High awareness" text #6B2FA3 on #F1E8FB;
   Tinted pill, same size, radius and font as the existing Window pills, with a small inline
   SVG warning triangle before the text (viewBox 24, stroke currentColor, stroke-width 2,
   round caps/joins): M12 4l9 16H3z  +  M12 10v4  +  M12 17.2v.3
   Styled tooltip (the console's own tooltip style, not the browser title): one line per
   overlapping period, "Name · Critical awareness · <d Mon HH:MM> – <d Mon HH:MM> ET"
   (or "High awareness"), ordered by level then start.

4) Review: At a glance and Calendar
   - At a glance: add an "Awareness" row when any period overlaps: level pill (same
     colours) plus the period names and dates. Omit the row when there is none.
   - Calendar: mark the awareness days with the same tint (critical amber, high violet)
     and the same tooltip text. Freeze markers keep priority where both apply.

5) Review decisions filter
   The segmented filter (All / Approve / On hold / Needs work / Not decided) shows text and
   counts only, no icons. Icons stay on the CRQ line and in the overlay.

6) Docs and version
   - Guide/docs: a short note on what awareness periods are, where they come from (the events
     calendar, kept by hand in calendar.yaml) and that they never affect the score.
   - CHANGELOG 0.57.0; pyproject version 0.57.0.
   - Tests: overlap (inside, partial, exact boundary, DST change, multi-period, highest level
     wins), config validation, pill/tooltip rendering, filter without icons, freeze pill
     colour and tooltip, pill order.

7) Freeze pill
   "Freeze" text #A61B1B on #FDE8E7 (same as the Blocked tag); "Freeze · exception"
   unchanged (neutral grey). Pill order on the Window line: Today/Tomorrow, then Freeze, then
   awareness. Freeze pills get the same styled tooltip: one line per overlapping restricted
   period "Name · Change Restriction · <d Mon HH:MM> – <d Mon HH:MM> ET", then "Blocked unless
   an approved freeze exception is recorded" (Freeze) or "Exception recorded in Work Detail
   (<type found>)" (Freeze · exception). Rename the freeze periods in calendar.yaml to the
   event names on the published calendar (e.g. "NOV Month End Processing"); dates and times
   unchanged.

Do not change: any rule, severity, score, window check (CC-10/11/12), freeze rule (CC-05)
logic, decisions storage, or existing behaviour outside the items above.

Verification (UI level): ruff; the tests for the changed modules; browser -k pending and
-k review. Do not run check.py --audit or --update-baseline. Report: files changed, test
counts, and the old -> new rule set ID if the config change moves it. Then stop.