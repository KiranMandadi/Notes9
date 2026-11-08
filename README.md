I've added organisations and groups to support_groups.yaml. Same standing rules (including Running commands); no git operations unless I ask. Do not print any organisation or group names; refer to them by position (org #n, group #n).
1. Validate: run crq rules validate and the support_groups loader; report pass/fail.
2. Typo check: for each NEW group, count its changes in Remedy over the last 90 days with an existing crq search option (read-only). Report "group #n: count". Flag any group with 0 as a possible name mismatch.
3. Update the pinned tests: tests/test_enterprise.py (lines 33 and 70, group count) and tests/test_screens.py (line 79, organisation list) to the new values.
4. Run python scripts/check.py; show me what fails. Do not run --update-baseline until I confirm.
5. Run the accuracy audit (python scripts/check.py --browser --audit); report mismatches (expect 0) and the new rule-set id.
6. Report the Pending load time (Console access log, POST /api/summary) before and after, and the new Pending total for all approvers.
CHANGELOG entry (no names, just counts: "support groups: +N organisations, +M groups"). Run all tests with pytest; report counts.
No branches, tags or commits.

git status
git add support_groups.yaml tests/baselines/enterprise.sha256 tests/test_enterprise.py tests/test_screens.py CHANGELOG.md
git commit -m "Support groups: add new organisations and groups"
git push