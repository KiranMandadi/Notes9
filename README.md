git add -A
git status
git commit -m "0.62.1: CV-17 accepts N/A as an answer" -m "- Roll Back ETA and User Restoration ETA answered N/A, not applicable, none, no users or
  no rollback needed count as answered (e.g. a new application with no users yet)
- Placeholders (TBD, TBA, ASAP, -, [todo]) still flagged
- How to meet it: give a time, or say N/A with the reason
- Rule set <old> -> <new>; baseline, docs, CHANGELOG and tests updated"
git push