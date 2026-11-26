git add -A
git status
git commit -m "0.60.1: window check checks tasks inside restricted periods again" -m "- Fix 0.60.0 regression: implementation tasks inside a restricted period were skipped,
  leaving 18 changes with a false 'no usable implementation task' advisory (CC-12 28 -> 10)
- Validation tasks never count as implementation (like certification); exclude wins over include
- CC-05 advisory: 'Check' label (new optional fix_label rule key) and clearer In scope wording;
  CC-12 fix names all window exception types; At a glance Freeze value in neutral colour
- Rule-file reader now keeps the new fix_label key
- Rule set 3eafd70b -> 84e11bfa (change-class 2.4.1); baseline, docs, CHANGELOG and tests updated"
git push