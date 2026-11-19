0.55.0 last polish. UI level (-k review). Panel: hide the rule description sentence when
it repeats "What was checked" (same meaning); remove the line "This rule is for every
change it applies to." from all would_change texts (leave would_change empty if nothing
else to say, and hide the line). Report rule set id. Then stop.

python scripts/check.py --update-baseline
python scripts/check.py --browser --audit
git status
git add -A
git status
git commit -m "0.55.1: explanation panel wording" -m "- Rule description hidden when it repeats 'What was checked'
- Removed the filler line 'This rule is for every change it applies to'
- Wording only: no score or verdict changes
- Rule set <old id> -> <new id>; baseline and CHANGELOG updated"
git push