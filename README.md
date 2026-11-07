Approved. Proceed with step 2:
- Make the content-word helper the default for Q-COMPLETE-04 and the audit check; remove the CHANGELENS_CONTENT_WORDS flag and any flag-off code path.
- Bump the rule pack's minor version and update the rule's description if it says how words are counted (e.g. "ticket keys, record numbers and single characters don't count as words").
- CHANGELOG and decisions.md: the fix, the word definition, and the measured impact (6,461 past changes: 0 mismatches, 4 findings removed, 7 added, 1 status change Needs work → Blocked). No change numbers in any file.
- Rerun the full suite and `python scripts/check.py --browser --audit`; expect 0 mismatches. Report counts.
- Delete work/tmp/words/ when done.
No branches, tags or commits.

git status
git add -A
git commit -m "Q-COMPLETE-04: count content words correctly (hyphenated words count; ticket keys, record numbers and lone characters don't). Audit mismatches 7 -> 0."
git push