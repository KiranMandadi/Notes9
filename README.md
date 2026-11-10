Go ahead: apply Option A to Q-VAGUE-01 exactly as measured (same word list and rules, Notes/Backout plan/Summary). Bump the core pack version; update the rules catalogue, user-guide and CHANGELOG (no new version). Add a test with the CRQ000002484053 pattern (claim, then a next sentence about what continues/is not impacted → no finding) and one where the next sentence only repeats "no impact" (→ finding stays).
Run python scripts/check.py --browser --audit and report: old and new rule set id; mismatches (expect 0); Q-VAGUE-01 findings removed on the audit set (expect 2: CRQ000002289292, CRQ000002299314) and score/status changes (expect 40→60 and 60→80, no status change); confirm nothing else changed. Do not run --update-baseline; I will. Run all tests with pytest; report counts. No branches, tags or commits.

python scripts/check.py --update-baseline
python scripts/check.py
git status
git add -A
git commit -m "Q-VAGUE-01: accept an explanation in the next sentence"
git push