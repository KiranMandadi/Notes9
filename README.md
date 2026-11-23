Read-only measurement: CV-18 (impact understated): deferral sentences and stated
justification. Do not change any code, rule, config or baseline.

Population: every change CV-18 currently fires on (Major), from live Remedy data via the
existing review path, same scope as the audit. Also count CV-18 advisories (Scheduled) separately.

For each finding, classify with two candidate checks (prototype them in a new script under
work/, not in cr_core):

A) Deferral exclusion. A sentence describes the cost of NOT deploying, so it must not count
   as reach: "without deploying", "not deploying", "if not deployed", "if we don't deploy",
   "if deferred", "deferring", "delay(ing) this", "not implementing", "failure to deploy",
   and sentences inside the "cannot be deferred" justification question. Re-run reach
   detection with those sentences removed. Does reach D still hold?

B) Stated justification. Within the Change Assessment (any question except the attestation
   question, which is never read or quoted), find a sentence that:
   1. names the stated Impact level (number 1–4 or its wording, e.g. "Moderate/Limited"), AND
   2. gives a reason (because / as / since / due to), AND
   3. the reason describes scope of who is affected: internal, non-customer-facing,
      no client/customer impact, reports/batch only, a single team, or a count of users
      ("tens of users", "few users", "<N> users").
   Also count separately: explicit "non customer facing" / "internal only" / "negligible"
   statements without the level named.
   Not a justification: a bare label, or generic reasons (risk is low, tested, rollback
   available, minimal risk).
   Contradiction: if a sentence about the change failing (not about deferral) names
   customers or clients being harmed, B does not apply.

Report codes and counts only:
- total CV-18 Majors; how many A alone clears (reach D no longer holds); how many B alone
  would downgrade to advisory; how many A or B; how many stay Major; how many B blocked by
  a contradiction.
- the same for the CV-18 advisories.
- distribution of which deferral phrases and which justification patterns matched.

Write a review list to work/cv18_review.md for me to spot-check: change number, which of
A/B applied, and the matched sentence (max 200 chars, from the Change Assessment only;
never the attestation answer, never Internal notes, no submitter names). I will delete it.
Do not print change numbers or quotes in chat.

Do not read cr_core/config.py, cr_core/history/config.py or .env. Never delete anything
under work/history/. No git operations. Any heredoc, python -c or python - is a stop
condition. Then stop and report.