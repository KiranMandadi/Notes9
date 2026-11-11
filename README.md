python scripts/check.py --update-baseline
python scripts/check.py
crq ui --restart

git status
git add -A
git commit -m "Remove the Executive brief; Quality report is the only report"
git push