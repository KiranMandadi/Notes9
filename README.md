python scripts/check.py --update-baseline
python scripts/check.py --browser --audit
git status
git diff --stat
git add -A
git status
git commit -m "0.52.2: cleanup, no behaviour change" -m "- Removed unused code: text_suggests_database builtin, starts_in option, two unused
  shapes, four unused CSS classes, OVERLAPS_CELL
- Stale comment in quality_rules.yaml corrected (baseline updated; rule set unchanged)
- Docs brought in line with 0.52.1: rule and pack counts, MF-05/CC-08 references, upgrade
  notes, rules-authoring example, open item D27
- Guide sample report uses a current finding (release name)
- Copilot instructions: never delete work/history/
- Rule set a281f7da unchanged; history findings, live scores and verdicts identical"
git push