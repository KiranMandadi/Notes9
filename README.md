Pending Status filter: add "Scheduled"; Exec Summary advisory on Scheduled changes. Same standing rules from .github/copilot-instructions.md; no git operations unless I ask. If you ask me something and get no answer, stop and wait. Exclude cr_core/config.py and cr_core/history/config.py from every search; summarise tracebacks instead of printing them. Do not run --update-baseline; I will.

1. Add Remedy status "Scheduled" to the Status filter, loaded on demand exactly like Planning In Progress: not ticked by default, shows "Loads when selected" until ticked, then fetched live from Remedy and scored like the rest; same spinner, failure + Retry, and Refresh behaviour.
2. Order in the popover (lifecycle): Planning In Progress, Scheduled For Approval, Scheduled. Default unchanged: Scheduled For Approval only.
3. Labels: "Status Scheduled For Approval" (default), "Status Scheduled", "Status 2 stages", "Status All stages" (all three).
4. URL: add the short code "scheduled"; no parameter for the default; old URLs keep working.
5. Everything downstream follows Status as today (headline count, filters, hidden-changes pill, calendar, Review decisions total).
6. Exec Summary on Scheduled changes: run the same Q-COMPLETE-10 check (same question, shortened-wording and labelled-section matching), but as an advisory (0 points, "Worth a look"), with the message ending "(advisory: the change is already approved)". Draft through Scheduled For Approval keep the Major. History replay stays excluded. Bump the affected pack version.

Tests (Remedy mocked): Scheduled unticked by default with "Loads when selected"; ticking it fetches only that stage; labels for each combination; URL round-trip; Refresh reloads it once loaded; Q-COMPLETE-10 is a Major for Scheduled For Approval and an advisory (0 points) for Scheduled.
Run ruff, unit tests, browser tests -k "pending or filter", and python scripts/check.py --audit (rules changed). Report: old/new rule set id, audit mismatches (expect 0), and how many loaded Scheduled changes get the advisory. Update user-guide (Status filter, Exec Summary note), rules catalogue, one CHANGELOG line.
No branches, tags or commits.

   python scripts/check.py --update-baseline
   python scripts/check.py
   git status
   git add -A
   git commit -m "Pending: Scheduled status on demand; Exec Summary advisory on Scheduled changes"
   git push