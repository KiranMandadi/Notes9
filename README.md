0.53.2 addition (baseline NOT updated). Quick level.
CV-18 message: show the actual restoration time the owner wrote, not the band label.
Format: 'with restoration of about <parsed time> (<source>: "<answer as written, <=30
chars>"; <other ETA> not given)' and then the band as the reason: 'over 1 hour of
customer impact suggests Impact 1 – ...'. Band reasons: "up to 15 minutes", "over 15
minutes", "over 1 hour", "over 4 hours". When neither ETA has a readable time: "no
restoration time given (treated as over 4 hours)". Use the longer of the two times and
name its source. Tests for each case incl. "~ 2 Hour" -> "about 2 hours". Report rule
set id. Then stop.


python scripts/check.py --update-baseline
python scripts/check.py --browser --audit
git status
git add -A
git status
git commit -m "0.53.3: CV-18 message quotes the owner's restoration time" -m "- CV-18 shows the restoration time as written (e.g. 'about 2 hours, Roll Back ETA')
  and names its source, instead of the band label ('up to 4 hours')
- The band is given as the reason for the suggested Impact (over 15 min / 1 h / 4 h)
- No restoration time: 'no restoration time given (treated as over 4 hours)'
- Wording only: no score or verdict changes
- Rule set <old id> -> <new id>; baseline, CHANGELOG and tests updated"
git push