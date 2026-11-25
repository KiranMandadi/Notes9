0.60.0: freeze becomes a warning; Restriction Exception completeness check.

STEP 0 (read-only, then STOP for my OK): on live data, same scope as the audit, report codes
and counts only: changes whose window overlaps a restricted period, split by In Scope
(Yes / No / blank); for In Scope = Yes, how many have a Restriction Exception Work Detail,
how many would be incomplete under rule 2 below, and which questions are unanswered (counts
by question wording); score/verdict changes before -> after. Write work/cc05_new_review.md
(change number, In Scope, exception present, unanswered question wordings; never answer text,
no names). Then stop.

STEP 1 (after my OK): build.

1) CC-05 (restricted period) becomes an advisory: no points, never a Blocker, shown under
   "Worth a look". Decided by the CHANGE WINDOW only (scheduled start/end); task times are no
   longer used for it. Messages:
   - In Scope = Yes: "The window falls in <period name> <start> – <end> ET. Restriction
     Exception recorded." Detail line: "Change window: <start> – <end> (inside the restricted
     period)".
   - In Scope = No: "The window falls in <period name> <start> – <end> ET; 'In scope of
     Restriction' is set to No." Same detail line.
   - In Scope blank: "The window falls in <period name> <start> – <end> ET; 'In scope of
     Restriction' is not set." Same detail line.
   Restriction Approval Notes no longer count for anything. Remove them from every message,
   fix text, "How to meet it", Guide and catalogue entry.

2) New rule (next free ID in the same pack; never reuse a retired ID), Major (-20):
   "Restriction Exception complete". Applies only when In Scope of Restriction = Yes.
   - No Restriction Exception Work Detail (non-Internal) -> finding: "'In scope of
     Restriction' is Yes but no Restriction Exception is recorded in Work Detail."
   - Otherwise read the latest Restriction Exception entry. Identify questions by their
     wording, not number:
       Why does this change activity need to be completed during the restriction period?
       Does your MD/A3 support and approve this request?
       Name of approving MD?
       Is this change fixing or preventing a production problem?
       What is the associated Incident/Problem ticket number?
       Is the change a Regulatory requirement that must install during the restriction period?
       Is the change a restriction processing requirement?
       Is there a major cost reduction or savings by installing the change during the
       restriction period?
     All must be answered, except the Incident/Problem ticket number, which is required only
     when "fixing or preventing a production problem" is answered Yes. Blank or placeholder
     answers count as unanswered. Finding lists the unanswered questions by wording:
     "Restriction Exception incomplete: '<question>' is not answered."
   - Privacy: the "Name of approving MD?" answer is only checked for presence; never quote,
     store, log or display it. Do not quote any answer text in findings.
   - Lifecycle as other Change Assessment rules: scored while awaiting approval, advisory
     once Scheduled. Standard, Latent, Emergency out of scope.
   - "How this was assessed": what was checked, what was found, why Major, what clears it.

3) Pending Window pill (one restriction pill, same precedence logic):
   - In Scope = Yes and exception complete: grey "Freeze · exception".
   - In Scope = Yes and exception missing/incomplete: red "Freeze" with lock.
   - In Scope = No or blank: grey "Freeze · not in scope" (or "Freeze · scope not set").
   Precedence: Freeze > Freeze · exception / not in scope > Critical > High.
   Tooltip: restricted period line, then "Restriction Exception recorded" / "Restriction
   Exception incomplete" / "Marked not in scope of restriction" / "In scope of Restriction
   not set". Remove "Blocked unless an approved freeze exception is recorded".
   Review At a glance "Freeze" row uses the same wording.

4) Field map: make sure "In scope of Restriction" (restriction_scope) is in
   remedy_field_map.yaml and read for every change.

5) Tests (made-up fixtures, no live data): window in/out/boundary; Yes + complete; Yes +
   missing WD; Yes + one unanswered; ticket blank with production-problem No (passes) and
   Yes (fails); placeholder answer; MD answer never appears in output; No and blank ->
   advisory only; Approval Notes ignored; task times inside freeze but window outside ->
   no advisory; Scheduled -> advisory; pill and tooltip per case.
6) Docs (rules catalogue, user guide, configuration), CHANGELOG 0.60.0, pyproject 0.60.0.

Verification: ruff; tests for changed modules; browser -k pending and -k review. Report old
-> new rule set ID and live before/after counts (codes and counts only).
Do not run --update-baseline or the audit. No git. Do not read cr_core/config.py,
cr_core/history/config.py or .env. Never delete anything under work/history/.
Any heredoc, python -c or python - is a stop condition.