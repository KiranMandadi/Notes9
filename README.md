One correction to 0.60.0: Restriction Approval Notes must stay an accepted exception type for
the window check (CC-10/CC-11/CC-12), as before; only the freeze check (CC-05/CC-13) stops
accepting it. Restore it in calendar.yaml's window-check exception types, CC-10's How to meet
it, docs/configuration.md and the tests. Report the live CC-10/CC-12 counts before/after this
correction (codes and counts only). Same rules; no git, no baseline.

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