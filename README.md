Report headline: always separate the "and N more" tail with a semicolon and the word "issue(s)", e.g. "…, answer Exec Summary question 3; and 2 more issues". UI text only. Tests: headline with 1 and with 2+ remaining issues. Run ruff and browser tests -k report. One CHANGELOG line. No branches, tags or commits.

python scripts/check.py --update-baseline
python scripts/check.py
git status
git add -A
git commit -m "Exec Summary and Risk 4–5 findings list the missing questions in full; Scheduled status on demand"
git push