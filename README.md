Before I commit 0.61.0, four items:

1) CV-18 time message: add the missing space before "Impact is still the Remedy default"
   (seen as "lower.Impact"). Check the count message and any other appended line too; add a
   test that appended sentences are separated by one space.

2) CV-18 time bands: add a first band "up to 15 minutes -> 4 (Minor/Localized)", so a
   restoration of 15 minutes or less gives no time-based finding. Bands become:
   <=15 min -> 4, <=1 h -> 3, <=2 h -> 2, >2 h -> 1. A user count still takes precedence over
   time. Update "How this was assessed", the user guide, tests (15 min and 16 min, 60/61,
   120/121 boundaries) and CHANGELOG 0.61.0.

3) Read-only check: does check.py --audit (and the Console's Pending / Review list) read every
   page of the Remedy search, or only the first 200? Report the audit's change count today.
   If it is capped at 200, stop and tell me; do not fix it yet.

4) Re-run the live after-comparison against rule set 84e11bfa on ALL pages (codes and counts
   only): CV-18 Major / advisory before and after, by source (count / time), and verdict
   changes. Report the new rule set ID.

Verification: ruff; crq rules validate; tests for changed modules plus test_security;
browser -k review. No git, no baseline, no audit. Do not read cr_core/config.py,
cr_core/history/config.py or .env. Never delete anything under work/history/. No heredocs
(not even empty ones), python -c, python - or stdin redirects. Delete any temporary files in
work/ at the end.


git add -A
git status
git commit -m "0.61.0: CV-18 is advisory and follows the Remedy Impact definition" -m "- CV-18 never scores: Impact is defined by users/customers affected; restoration time only
  indicates it
- A stated user count with harm or unavailability (users, customers, clients, employees...)
  is compared with the definition first: 1000s -> 1, 100s or a workgroup -> 2, 10s -> 3, <10 -> 4
- Time bands: up to 15 min -> 4 (no finding), up to 1 h -> 3, up to 2 h -> 2, over 2 h -> 1
  (User Restoration ETA, else Roll Back ETA); no readable time -> no suggestion
- An explained Impact gives no finding; message notes when Impact is still the Remedy default 4
- Fix: At a glance lock icon no longer writes the SVG namespace URL (0.60.2 slip)
- Rule set 84e11bfa -> <new> (team-validation 2.4.x); baseline, docs, CHANGELOG and tests updated"
git push