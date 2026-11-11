Remove "Question for the owner" completely. Same standing rules from .github/copilot-instructions.md; no git operations unless I ask. If you ask me something and get no answer, stop and wait.
1. Remove the "Question for the owner" section from the Quality report (standalone page and Pending overlay), and the "· N question(s) for the owner" part of the report's summary line.
2. Delete the code that builds and renders owner questions (templates, view/render helpers, JS/CSS, API fields) and any CLI or Executive summary output of them. Keep any helper the Quality report or Executive summary still uses for something else.
3. STOP and ask before changing anything if owner questions are defined in the rule pack (YAML), affect scoring/findings, or are used by a Copilot agent — tell me where and what removing them would change.
4. Remove mentions from docs (user-guide, contracts, README, agents section) and tests; add a one-line docs/decisions.md entry ("Question for the owner removed: not used by reviewers") and a CHANGELOG line (no new version).
Tests: UI tier — ruff, unit tests for touched modules, browser tests for the report and overlay (-k report or overlay). Confirm the rule set id is unchanged. List anything you decided under "Decided".
No branches, tags or commits.

git status
git add -A
git commit -m "Remove Question for the owner from the report"
git push