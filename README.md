python scripts/check.py --update-baseline
python scripts/check.py --browser --audit
git status
git add -A
git status
git commit -m "0.54.1: Change Assessment severity by question; checklist layout" -m "- CV-15: Major when a core question is missing or unanswered (Deployment Strategy,
  Roll Back Type and ETA, User Restoration ETA, Business Impact, Attestation) or 3+
  questions are; otherwise Minor. Core and supporting lists in config
- Live: 30 of 55 findings Major -> Minor; 25 changes Needs work -> Ready; none worse
- Checklist (Technical details) on its own line above the notes, with a legend; notes
  keep full width
- Rule set c9143569 -> 57e6af7f; baseline, docs, CHANGELOG and tests updated"
git push