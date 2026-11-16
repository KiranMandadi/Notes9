Cleanup (0.52.2). Apply the inventory's candidates marked delete/rewrite/rename (not those
marked "leave"), plus N6. Do NOT do N1-N5 or N7.
Constraints unchanged: never read/search/print cr_core/config.py, cr_core/history/config.py
or .env; no Remedy writes; no crq login; no git; no inline Python — scripts in a file under
work/, deleted after; do NOT run --update-baseline; chat shows codes, counts and file paths
only.

Scope:
- Dead code: text_suggests_database builtin, starts_in option, unused shapes
  standard_template_number and version_three_part, four unused CSS classes, OVERLAPS_CELL,
  and the other C/Q items marked delete. Only if they truly have no callers/references.
- Stale comments: quality_rules.yaml CC-04 "please confirm" note, and other comment-only
  fixes (comments must not change parsed YAML).
- Docs: configuration.md (MF-05 reason list), user-guide rule/pack counts (82 rules; correct
  pack count), operations.md upgrade row for 0.52.1 and 0.52.2, rules-authoring.md (replace
  the CC-08 example with a current rule; describe question: accurately as stored, not shown),
  open item D27 (CV-08 counts after the Standard exclusion), and the other D items marked
  rewrite. Version 0.52.2 in pyproject and CHANGELOG ("Cleanup: no behaviour change").
- N6: Guide sample report — replace "Minor · Window longer than 8 h" with
  "Minor · The change doesn't name the release"; sample score stays 75.
- Tests: remove only tests that test deleted code (list each); rename misleading
  "fallback" test names; never weaken an assertion.
- work/: delete all old entries, including the three files holding change data. Confirm
  work/ is in .gitignore.

PROOF OF NO BEHAVIOUR CHANGE (all required; stop and report if any differs):
1) Rule set id unchanged: a281f7da.
2) Before and after, run the history audit and save per-change findings (rule id, severity,
   message) to work/ files: identical — same 17,661 findings, 0 differences.
3) Live: the same 4,483 changes — every score and verdict identical before and after.
4) ruff clean; full suite passes (report counts before/after and every removed test with
   its reason); browser tests same result (only the known 390 px failure).
5) scripts/check.py --browser --audit passes WITHOUT a baseline update.
Delete the comparison files after. Report files changed, items done/skipped, and the proof
results. Then stop.


git status
git diff --stat
git add -A
git status
git commit -m "0.52.2: cleanup, no behaviour change" -m "- Removed unused builtins, options, shapes, CSS classes and test constants
- Docs brought in line with 0.52.1: rule counts, MF-05/CC-08 references, upgrade notes,
  rules-authoring example, open items
- Guide sample report uses a current finding
- work/ emptied
- Rule set a281f7da unchanged; findings, scores and verdicts identical"
git push