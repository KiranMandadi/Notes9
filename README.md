Remove the Executive brief completely. Management confirmed it will never be used; the Quality report is the only report. Same standing rules from .github/copilot-instructions.md (including Running commands); no git operations unless I ask. If you ask me something and get no answer, stop and wait. No scoring change: rule set id must stay the same and the audit must show 0 mismatches.

Step 1 — inventory, then STOP and wait for my go-ahead:
List every place the Executive brief exists: templates, JS/CSS, server routes/API, report-building code, CLI commands/options, Copilot agent files, tests, screenshots, docs (user-guide, contracts, decisions, README), CHANGELOG mentions. For each, say: delete, or keep because the Quality report / CLI also uses it (name what uses it). Flag anything the "executive summary" CLI output or render.py shares with the brief.

Step 2 — after my OK:
1. Delete everything marked delete. Keep shared code the Quality report uses.
2. Review landing page: remove the "Open with" choice and its note. "Ready in seconds" card text: "A full quality report with clear next steps for each issue, plus context on risk, schedule and similar past changes. Ready to read on screen or share."
3. Report page and Pending overlay: no tab row (only the Quality report remains); tidy spacing between the header band and the report.
4. Old links and bookmarks that opened the brief (tab parameter, direct path) show the Quality report, no error.
5. CLI: remove brief commands/options; if one is called, print "The Executive brief has been removed; use the Quality report." and exit cleanly.
6. Docs: remove brief sections; add a docs/decisions.md entry ("Executive brief removed: management confirmed only the Quality report is used; last version is in git history before this commit").
7. Run python scripts/check.py --browser --audit (0 mismatches, same rule set id) and all tests with pytest; report counts and the rule set id. Update screenshots; CHANGELOG (no new version).
No branches, tags or commits.

git status
git add -A
git commit -m "Remove the Executive brief; Quality report is the only report"
git push