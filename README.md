0.58.0: CV-18 (impact understated): ignore cost-of-not-deploying sentences, and downgrade
to an advisory when the Impact level is explicitly justified.

1) Deferral exclusion. When CV-18 reads the Business Impact answer for reach, ignore any
   sentence describing the cost of NOT deploying: "without deploying", "not deploying",
   "if not deployed", "if we don't deploy", "if deferred", "deferring", "delay(ing) this",
   "not implementing", "failure to deploy". Those sentences never count as customer or
   business-function reach.

2) Stated justification. If the Change Assessment (any question except the attestation
   question, which is never read or quoted; Internal entries never read) has a sentence
   that names the stated Impact level (its wording, e.g. "Moderate/Limited", "moderate"
   near "impact", or the number tied to "impact"/"level", not followed by min/hour/day),
   gives a reason (because / as / since / due to), and the reason describes scope (internal,
   non-customer-facing, no client/customer impact, reports/batch only, a single team, or a
   count of users), then CV-18 is an advisory (score 0) instead of Major.
   Not a justification: a bare label, or generic reasons (low risk, tested, rollback
   available, minimal risk).
   Contradiction: if a sentence that is not about deferral passes the CV-18 harm test with
   customers, clients, investors or account holders named (a business function alone
   doesn't count), the justification does not apply and the Major stays.

3) Messages (neutral wording, no question numbers, no format or version wording):
   Advisory: "The Impact is stated as <n> – <wording> and explained in the Change
   Assessment: "<justification, max 160 chars>". The worst case and restoration time would
   otherwise suggest Impact <m> – <wording>; confirm the explanation holds."
   "How this was assessed" for the advisory: what was checked (worst case, restoration
   time, stated Impact), what was found (implied level, the justification sentence), why
   advisory (the change explains its Impact level), what would make it Major (no
   explanation, or a sentence showing customer harm from the change).
   Major wording unchanged.

4) Lifecycle and scope unchanged (scored while awaiting approval, advisory once
   Scheduled; Standard, Latent and Emergency out of scope).

5) Tests with made-up fixture text (no live data): each deferral phrase excluded; a
   deferral-only "clients" sentence no longer gives reach; justification with level word,
   with number, with "3 – Moderate"; justification missing a reason, missing scope, generic
   reason → stays Major; contradiction sentence keeps Major; "3 hours" not read as Impact 3;
   attestation text never read; Scheduled stays advisory.
6) Docs (rules catalogue, user guide impact section), CHANGELOG 0.58.0, pyproject 0.58.0.

Verification: ruff; tests for the changed modules; browser -k review. Report the old -> new
rule set ID and, on live data, the CV-18 counts before/after (codes and counts only).
Do not run --update-baseline or the audit. Do not read cr_core/config.py,
cr_core/history/config.py or .env. Never delete anything under work/history/. No git.
Any heredoc, python -c or python - is a stop condition.


git commit -m "0.58.0: CV-18 reads cost-of-not-deploying and stated Impact justification" -m "- CV-18 ignores sentences about the cost of not deploying when judging customer reach
- An explicit Impact justification (level, reason, scope) turns CV-18 into an advisory;
  a sentence showing customer harm from the change keeps it Major
- Advisory message and How this was assessed explain the downgrade
- Rule set <old> -> <new>; baseline, docs, CHANGELOG and tests updated"