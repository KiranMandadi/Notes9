python scripts/check.py --update-baseline
python scripts/check.py --browser --audit

git status
git diff --stat
git add -A
git status
git commit -m "0.52.0: Window check from Remedy window fields" -m "- CC-10 (Major): implementation task outside its allowed window. Authorized hours
  (Mon-Fri 20:30-07:00, Sat-Sun and holidays 14:00-07:00 ET) plus the declared
  Specialized window, read live from Remedy per request (no cache)
- Majors only where the data proves it; uncertain cases are CC-12 advisories (Emergency,
  window type not set, task copies the change window, task over 24 h, 30-min start
  grace, possible exception in notes, no usable implementation task, hours unavailable)
- Window exceptions recorded in Work Detail (Restriction Approval Notes, Restriction
  Exception, Windows Exception) clear the finding
- CC-11 (Minor): window type not set past Draft, or Specialized with no window
- Retired MF-05, CC-07, CC-08 and the placeholder mainframe/business-hours/weekend periods
- Cancelled and Rejected changes skipped; stale and freeze-flagged tasks excluded
- Rule set 6dc76797 -> d1a893eb; baseline updated; docs, CHANGELOG and tests updated"
git push