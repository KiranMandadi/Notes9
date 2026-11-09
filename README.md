CV-03 to advisory. Same standing rules (including Running commands); no git operations unless I ask. If you ask me something and get no answer, stop and wait.
1. In common-validation.yaml, change CV-03 from active Minor to advisory (shown under "Worth a look", 0 points). Condition unchanged: fires when Risk Level - Computed reads High (4 or 5).
2. Message: "Aggregate risk is {value} – {legend}." (legend: 1 Minimal, 2 Low, 3 Medium, 4 High, 5 Extreme). Fix text: "Make sure the Notes explain the risk and how it is controlled."
3. Bump the pack version. Close D32 in docs/open-items.md: CV-03 reads Risk Level - Computed (the aggregate in Remedy's Change Risk Report).
4. Run python scripts/check.py --browser --audit and report:
   - old and new rule set id;
   - how many changes had CV-03 removed from their scored findings, and confirm every score difference is exactly +5 from CV-03 and nothing else;
   - how many changes changed status (from → to, counts only).
   Do not run --update-baseline; I will after reviewing.
Update tests, the rules catalogue and user-guide; CHANGELOG (no new version). Run all tests with pytest; report counts.
No branches, tags or commits.