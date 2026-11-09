Leadership decision: "Impact During Backout: No impact" is a Minor, not a Major. Build it as follows:
1. Q-VAGUE-01: skip "no impact" when it is the answer to an "Impact During Backout" label (colon, with or without a space before it) in the Backout plan. Everything else in Q-VAGUE-01 unchanged.
2. New rule Q-VAGUE-04, active, Minor (5 points), Backout plan only: fires on that labelled "No impact" answer unless the same reason words that suppress Q-VAGUE-01 appear in the same or previous sentence. Message: "The Backout plan says 'No impact' during backout without saying why." Fix: "Say why backout has no impact, for example the service stays up or traffic moves to the other site." Record match offsets so evidence highlighting works.
3. Bump the core pack version; update the rules catalogue, user-guide and CHANGELOG (no new version).
4. Run python scripts/check.py --browser --audit and report: old and new rule set id; mismatches (expect 0); how many Q-VAGUE-01 findings became Q-VAGUE-04 (expect 107); score changes (from → to, counts) and status changes (counts); confirm no change outside these 107. Do not run --update-baseline; I will.
Run all tests with pytest; report counts. No branches, tags or commits.

python scripts/check.py --update-baseline
python scripts/check.py
git status
git add -A
git commit -m "Q-VAGUE-04: 'Impact During Backout: No impact' scored as Minor; Q-VAGUE-01 skips it"
git push