If any test or script reached the real Console on port 8765, fix it so tests only ever use their own test server/port, and add a guard test for that. Delete scripts/status_load.py after the before/after measurement.   
   
   git status
   git add -A
   git commit -m "Fix /api/status pile-up; search card: hard input limits, no footer line"
   git push