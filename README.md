full gate + release 0.47.0. Same standing rules; no git operations unless I ask. Exclude cr_core/config.py and cr_core/history/config.py from every search. Do not run --update-baseline; I will if needed.
1. Bump the version from 0.46.0 to 0.47.0 everywhere it is defined or shown (package metadata, __version__, Console footer/status, docs that state the current version). Find every occurrence of "0.46.0" and list them; change only those that mean the current version (leave history entries alone).
2. CHANGELOG: turn the unreleased/0.46.0-in-progress entries since the 0.46.0 release into a "0.47.0 — 12 Nov 2026" section with a short summary at the top (rules: freeze windows, Risk Level 4–5 questions, Exec Summary checks incl. labelled sections, CV-02 advisory; Pending: Risk filters, Status values, filter highlighting, Refresh feedback; reports open in place; readability scale; Remedy link; Executive brief and owner questions removed).
3. Full gate: python scripts/check.py --browser --audit, all tests with pytest, retake the docs screenshots (including the outdated Pending one), docs pass for anything still describing removed features.
4. Report: every file changed for the version bump, audit mismatches, rule set id, test counts, and anything I must do (e.g. baseline update if the version is pinned).
No branches, tags or commits.

python scripts/check.py
git status
git add -A
git commit -m "Release 0.47.0"
git push