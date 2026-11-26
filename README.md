OK, continue and finish: docs/configuration.md, docs/contracts.md, docs/rules-authoring.md,
CHANGELOG 0.60.0 (also mention CC-09 retired), pyproject 0.60.0, the final verification,
the live after-comparison against work/cc05_before.json (codes and counts only), then delete
work/cc05_before.json, work/cc05_snapshot.py and work/cc05_new_review.md. Your decisions are
approved. Same rules: no heredocs (not even empty ones), python -c, python - or stdin
redirects.


git add -A
git status
git commit -m "0.60.0: freeze is a warning; Restriction Exception must be complete" -m "- CC-05: restricted period is an advisory (no points), decided by the change window only;
  message states the In scope of Restriction value
- CC-13 (new, Major): In scope of Restriction = Yes needs a complete Restriction Exception;
  N/A accepted, ticket number required when fixing a production problem; answers never quoted
- CC-09 retired; Restriction Approval Notes no longer count
- Pending pill and tooltip: Freeze / Freeze · exception / Freeze · not in scope / scope not set
- Rule set 45dd2aa5 -> a9fc5042; baseline, docs, CHANGELOG and tests updated"
git push