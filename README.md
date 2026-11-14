Rules page (UI only):
1) Remove the "OWNER" label and owner value from every rule-pack card header.
2) Header stats line: "81 rules · 13 rule packs · 7 owning teams" → "81 rules · 13 rule packs"
   (counts computed as now).
3) Subtitle: replace "Scoring weights and thresholds are ChangeLens defaults, to be confirmed
   with the Change Management office." with "Scoring weights and thresholds are ChangeLens
   defaults and can be adjusted in the rule packs."
4) Search the Console UI (rules page, report, tooltips, help text) and the user guide for any
   other visible mention of "Change Management office" or "owning team(s)" and list them in
   your report; change UI/user-guide wording only where it presents the CM office as an owner
   or approver.
Do NOT change rule-pack YAML (keep the owner field), rule IDs, scoring or the rule set id
(must stay unchanged). Run the Rules page browser tests and ruff only. Report files, the
mentions found, and counts; then stop. No git.

git status
git diff --stat
git add -A
git status
git commit -m "Rules page: remove owner; update subtitle" -m "- Owner removed from rule-pack cards and 'owning teams' from the header stats
- Subtitle: defaults can be adjusted in the rule packs (no CM office wording)
- Rule packs, rule set id and scoring unchanged"
git push