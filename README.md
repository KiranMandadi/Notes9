0.56.1: explanation panel accuracy and wording (baseline NOT updated). Quick level (ruff +
tests for changed modules; browser -k review only for the header). No heredocs, python -c
or python -.
1) GEN-03 (and any rule that can match in the Change Assessment): include "Change
   Assessment" in the "Searched:" list and say where it was found ("found in Change
   Assessment"). Please confirm reason: "No points: <what> are named in the Change
   Assessment, but ChangeLens can't tell whether they cover this release. Confirm they
   do; if not, add them." Remove the "counts as Minor" sentence.
2) CC-05: issue sub-line "Change window: <window> (inside the restricted period)" instead
   of "Restricted: <window>". How to meet it lists only the restricted period(s) the
   change clashes with and those still to come; never past periods.
3) Exec Summary rules (Q-COMPLETE-10/-11/-12): How to meet it = "At the top of the Notes,
   answer the three Exec Summary questions: <the three questions>. 'No' is an answer;
   'N/A', 'TBD', 'None' or '-' are not." Remove matching details (labels, headings, '?' or
   ':', key words). Keep those details in the rules catalogue/docs only.
4) CV-15 Minor reason: "Minor: only a supporting question is missing." (or "…questions
   are missing" when 2). Keep would_change as is.
5) Panel header shows the rule id only (e.g. "CV-15"); drop pack name and version there.
6) Scan all How to meet it / why texts for matching internals or past dates; report any
   changed. CHANGELOG 0.56.1; pyproject 0.56.1. Report rule set id. Then stop.


   python scripts/check.py --update-baseline
python scripts/check.py --browser --audit
git status
git add -A
git status
git commit -m "0.56.1: explanation panel accuracy and wording" -m "- GEN-03: Change Assessment shown as searched and where it was found; clearer Please
  confirm reason
- CC-05: change window labelled as such; How to meet it lists only relevant restricted
  periods
- Exec Summary: How to meet it in plain terms, no matching details
- CV-15 Minor reason simplified; panel header shows the rule id only
- Rule set <old id> -> <new id>; baseline and CHANGELOG updated"
git push