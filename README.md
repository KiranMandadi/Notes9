Pending: remove the automatic fallback to all approvers.

Today, when nothing awaits the configured/default approver (state.chose = false), who() falls
back to all approvers and shows the yellow note "Nothing is awaiting <name> right now, so all
approvers are shown." Change this:

1) The page always lands on the configured approver, even with 0 changes. who() returns the
   configured approver unless the user explicitly chose "All approvers" (Show all approvers
   link, Approver chip, or a saved view). No automatic switch, ever.
2) Remove the yellow fallback note and its code/CSS.
3) The 0-changes screen stays exactly as it is today: headline "<name> · 0 changes",
   "Show all approvers" link, Approver chip = <name>, "Showing 0 of 0", empty-table message
   "No changes match the filters. Clear search and filters". No visual changes.
4) Same in Calendar view.
5) Unchanged: when no default approver is configured, the page shows all approvers as today;
   Show all approvers / Show only <name> links; Clear all; saved views (flag on or off);
   ORR/Risk Level defaults per approver.

Tests: update tests that expect the fallback; add tests for (a) configured approver with 0
changes stays on that approver with no note, (b) Show all approvers still works from there,
(c) no configured approver still shows all approvers. Run only the Pending browser tests and
ruff. Update CHANGELOG (under 0.48.0) and the user guide line that describes the fallback.
Report files changed and counts, then stop. No git.


git status
git diff --stat
git add -A
git status
git commit -m "Pending: no auto-fallback to all approvers; Quality score 13 px" -m "- Pending always lands on the configured approver, even with 0 changes
- Yellow fallback note removed; Show all approvers stays one click away
- Quality score 13 px, tabular numbers
- Tests, user guide and CHANGELOG (0.48.0) updated"
git push