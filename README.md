0.61.1: read every page of the Remedy search.

Today every list read from Remedy stops at the first page (200 changes). Make ChangeLens keep
asking for the next page until Remedy has no more results.

1) Find every place that reads a list of changes from Remedy (at least: the Pending list in
   all filters and views, the overlap check in the Console, the overlap check in
   check.py --audit). Report the list before changing anything.
2) For each, page through the Remedy search until all matching changes are read. Requests one
   after another (not in parallel), same page size as today. Add a safety cap of 5,000
   changes; if it is ever reached, stop and show a clear message ("More than 5,000 changes
   match; narrow the filters").
3) Remove the "more changes than shown" note when all pages were read; keep it only when the
   safety cap is hit.
4) No change to rules, scoring, caching or what is shown for each change. Shared mode still
   reads live Remedy data for every request (no cache).
5) Tests: a fake Remedy returning 450 results across 3 pages -> Pending shows 450 and the
   overlap check sees all 450; exactly 200 results -> a single extra empty-page check, no
   error; the safety-cap message.
6) Docs where the 200 limit is mentioned; CHANGELOG 0.61.1; pyproject 0.61.1.

Verification: ruff; tests for changed modules plus test_security; browser -k pending.
Report: the places changed, the live count for Status = Scheduled For Approval + Scheduled
(expected about 303, all shown), how long the Pending list takes to load now vs before, and
whether the rule set ID changed (it should not).
No git, no baseline, no audit. Do not read cr_core/config.py, cr_core/history/config.py or
.env. Never delete anything under work/history/. No heredocs (not even empty ones),
python -c, python - or stdin redirects.