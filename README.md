0.53.0 fixes before commit (baseline still NOT updated). Usual constraints; codes and
counts only; no answer or attestation text.

1) Q9 by position: a heading whose text is "Justification" (any case, optional number,
   optional colon) that appears AFTER the Q8 heading counts as Q9. The first
   Justification before Q2 stays Q1. Also accept "Justification (if N to #8)" and similar.
   Tests: "8. Can this be deferred 3 to 5 days? / (Y/N): No / justification: / <text>"
   -> Q8 = N, Q9 answered, no finding; Justification only at the top and Q8 = N with
   nothing after -> Q9 missing.

2) Wording — no question numbers in findings or fix text (numbers stay only in the
   Technical-details checklist line, with names in tooltips). Use the CAB wording as
   short names in config:
   Q1 "Justification", Q2 "Deployment Strategy", Q3 "Deployment Type", Q4 "Roll Back
   (Backout) Type and ETA", Q5 "User Restoration ETA", Q6 "Business Impact (worst case
   scenario)", Q7 "Rollback/Backout Plan Attestation or Validation Sign-Off", Q8 "Can this
   be deferred 3 to 5 days? (Y/N)", Q9 "Justification on why the change cannot be
   deferred".
   - Missing: issue 'Change Assessment incomplete: "User Restoration ETA" and "Can this be
     deferred 3 to 5 days? (Y/N)" are missing.' fix 'Add "User Restoration ETA" and "Can
     this be deferred 3 to 5 days? (Y/N)" to the Change Assessment Work Detail, and answer
     each.'
   - Unanswered: issue 'Change Assessment: "Deployment Strategy" has no answer.' fix
     'Answer "Deployment Strategy".'
   - Q9: fix 'Explain why the change cannot be deferred under "Justification on why the
     change cannot be deferred".'
   - Combine missing + unanswered in one finding; 4 or more items -> bullet list.
   - Verdict headline stays short: "Complete the Change Assessment (2 questions missing,
     1 unanswered)".
   - CV-16: 'Answer "Can this be deferred 3 to 5 days? (Y/N)" with Y or N.'
     CV-17: 'Give a time in minutes or hours for "Roll Back (Backout) Type and ETA".'
     (or "User Restoration ETA").
   - CV-14 fix: "Add a Change Assessment Work Detail answering each CES CAB question."
   - Exec Summary rule: same approach — headline/fix use short names ("What is changing
     and why", "How production impact is controlled", "Exceptional recovery risk"), body
     keeps the full question text as today; never "above" or "questions 1, 2 and 3".

3) Measure on live (awaiting approval): CV-15 findings naming Q9 before and after fix 1;
   any other CV-15 that disappears or changes (should be 0).
4) Rerun the browser tests once; report whether the 4 Pending layout failures persist
   (do not change those tests).

Tests: update fix/issue text tests for every case above; no digits-as-question-numbers
in finding text. Verify: ruff, full suite, check.py --browser --audit (report the new
rule set id). Then stop.