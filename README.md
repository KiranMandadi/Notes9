0.64.0: Change Assessment template wording (new Minor rule) and deferral reading fix.

1) New rule (next free CV id), Minor (-5), one finding per change:
   "Change Assessment questions match the template wording".
   - A heading matches when, after ignoring numbering (1., 1), 4A., Q4), a leading bullet
     ("o", "•", "-"), case, whitespace, punctuation, bold markers, a bracketed "(Y/N)" and
     a trailing "-", ":" or "Y/N", its words are exactly the template's. Typos and different
     words are reworded.
   - Only questions present but reworded count. Missing questions stay with CV-15; no
     Change Assessment stays with CV-14. Internal entries are never read; if the Change
     Assessment is only in an Internal entry, this rule does not fire.
   - Answers are still read by meaning (no change to CV-15/16/17/18).
   - Message: "<n> Change Assessment questions don't match the template wording:" then one
     line per question "'<heading as written>' → '<template wording>'" (max 9 lines;
     headings max 80 chars; never the attestation answer).
   - Fix: "Use the current Change Assessment template wording for these questions."
   - Scope and lifecycle as other Change Assessment rules (scored while awaiting approval,
     advisory once Scheduled; Standard, Latent, Emergency out of scope).
   - "How this was assessed": what was checked, what was found, why Minor ("the answers
     are still read; this keeps the questions as the CAB template sets them").
2) Deferral reading fix: skip template prompt lines with no answer ("Y/N", "(Y/N)",
   "Y/N, Justification", "Justification" alone) and read the next line. Accept "Yes"/"No"
   (with a reason after it) as Y/N; "Y/N" alone stays unanswered.
3) Tests: each ignored formatting case matches; typo and "rescheduled" are reworded; split
   "Roll Back Type"/"Roll Back ETA" reworded; Internal-only assessment -> no finding; one
   finding per change listing all; deferral "Y/N, Justification" then "Yes, ..." -> Y.
4) Docs (rules catalogue, user guide with the template wording list), CHANGELOG 0.64.0,
   pyproject 0.64.0.
Verification: ruff; crq rules validate; tests for changed modules plus test_security;
browser -k review. Report old -> new rule set ID; live counts (all pages, codes and counts
only): new rule findings (scored / advisory), CV-16 before -> after, score and verdict
changes. No git, no baseline, no audit. Usual rules: no heredocs, python -c, python - or
stdin; do not read the config files or .env; never delete anything under work/history/.
Delete work/ca_wording_review.md at the end.


git add -A
git status
git commit -m "0.64.0: Change Assessment questions must match the template wording" -m "- New Minor rule: reworded Change Assessment questions are listed once per change with the
  template wording to use; answers are still read by meaning
- Numbering, bullets, case and punctuation are ignored; different words and typos are not;
  Internal entries are never read
- Deferral question: template prompt lines are skipped; Yes/No with a reason counts as Y/N
- Rule set <old> -> <new>; baseline, docs, CHANGELOG and tests updated"
git push