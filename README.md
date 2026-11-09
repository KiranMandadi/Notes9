Option 1. Change the CV-03 text in the pack and bump the pack version. Expect a new rule set id; the audit must still show 0 mismatches. Do not run --update-baseline; I will. Then do the rest of the request, and report the old and new rule set id and the audit result.


git status
git add -A
git commit -m "At a glance: Risk Report group with aggregate risk value and ORR; flag when Risk Level differs"
git push