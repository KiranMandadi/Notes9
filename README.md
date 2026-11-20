python scripts/check.py --update-baseline
python scripts/check.py --browser --audit
git status
git add -A
git status
git commit -m "0.56.0: On hold decision, decision summary, explained 'no impact'" -m "- 'No impact' rules judge the whole answer: reported only when bare; an explanation in
  the following sentences now counts
- New review decision 'On hold' (Approve / On hold / Needs work) in the overlay and on
  Pending rows; own filter and count; keyboard H
- Decision icons as one set (bold check, clock, pencil); row tooltips without shortcut
  letters; no tooltips on the labelled overlay buttons
- Pending row controls (decision, copy, Remedy) hide when the pointer leaves the row;
  styled tooltips 'Copy' / 'Copied' / 'Open in Remedy'
- Copy decisions: heading with the date, counts (Approved, On hold, Needs work),
  'Decision' column coloured by outcome
- Larger labels on the Blockers / Major / Minor tiles
- Rule set 600c2731 -> <new id>; baseline, Guide, user guide, CHANGELOG and tests updated"
git push