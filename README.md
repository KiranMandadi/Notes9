0.53.0 last fixes before commit (baseline still NOT updated). Usual constraints.
1) Q-COMPLETE-08 fix text: name the questions instead of "above" (short names, same style
   as the Exec Summary fix).
2) Q-COMPLETE-11 highlight labels: use the short question names instead of "Question n".
3) Pending layout browser tests (the 4 scrollbar failures): measure available width
   without the scrollbar (e.g. documentElement.clientWidth or a scrollbar-free viewport).
   Do not lower any expected value or loosen any assertion; explain the change.
Run ruff, full suite, check.py --browser --audit; report the rule set id and browser
result (only the known 390 px test may fail). Then stop.

python scripts/check.py --update-baseline
python scripts/check.py --browser --audit
git status
git diff --stat
git add -A
git status
git commit -m "0.53.0: Change Assessment completeness (CES CAB standard)" -m "- CV-14 (Major): no Change Assessment Work Detail
- CV-15 (Major): one finding naming each missing or unanswered CAB question by its own
  wording; deferral justification by position; attestation checked for presence only
- CV-16 (Minor): deferral answer not Y/N; CV-17 (advisory): ETA without a readable time
- Scored while awaiting approval, advisory once Scheduled; Standard, Latent and Emergency
  out of scope; 'Change Regress Reason' entries skipped; not checked in history replay
- Link from findings to the Change Assessment entry; headings bold as whole phrases;
  Technical-details checklist; Notes labels no longer split
- Exec Summary and Notes fixes name the questions instead of numbers or 'above'
- Pending layout tests measure width without the scrollbar
- Rule set a281f7da -> <new id>; baseline, docs, CHANGELOG and tests updated"
git push