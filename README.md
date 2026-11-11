True, with one check first: confirm ask_owner, freeze_view, _schedule_box and _sentence are not used by the Quality report (it shows "1 question for the owner" and the freeze clash line). Keep any helper the Quality report or the Executive summary uses; delete the rest as listed.


python scripts/check.py --update-baseline
python scripts/check.py
git status
git add -A
git commit -m "Remove the Executive brief; Quality report is the only report"
git push