0.61.0: CV-18 (Impact may be understated) becomes advisory and follows the Remedy Impact
definition (number of users affected).

Remedy Impact definition (source of truth):
  1-Extensive/Widespread: 1000's of users/customers
  2-Significant/Large: 100's, or an entire workgroup
  3-Moderate/Limited: 10's of users/customers
  4-Minor/Localized: <10 users/customers (Remedy default)

STEP 0 (read-only, then STOP for my OK). Live data, same scope as the audit, codes and
counts only:
- current CV-18 findings (Major / advisory);
- under the new logic below: how many keep an advisory, from a user count vs from time;
  how many clear; how many Majors become advisories; verdict changes (Blocked / Needs work /
  Ready) before -> after;
- how many Change Assessments state a user count, by matched pattern and implied level.
Write work/cv18_v2_review.md (change number, stated Impact, count phrase or restoration
time, implied level, old result, new result; quotes max 160 chars from the Change Assessment
only, never the attestation answer, no names). Then stop.

STEP 1 (after my OK): build.
1) Severity: CV-18 is always an advisory (0 points), at every stage. No Major.
2) Reach gate unchanged: only when the worst case harms customers or a business function;
   cost-of-not-deploying sentences still ignored (0.58.0).
3) User count first. If the Change Assessment (any question except the attestation question)
   states how many are affected, map it with the definition: 1000s / thousands / all
   customers or clients -> 1; 100s / hundreds / an entire workgroup, team or department -> 2;
   10s / tens / dozens -> 3; fewer than 10 / a few / a handful -> 4. Explicit numbers map by
   the same bands. If the count implies a higher Impact (lower number) than stated ->
   advisory. A count that implies the same or lower Impact -> no finding. When a count is
   found, time is not used.
4) Otherwise restoration time (User Restoration ETA, falling back to Roll Back ETA):
   up to 1 hour -> 3; over 1 hour up to 2 hours -> 2; over 2 hours -> 1. No readable time ->
   no time-based suggestion (CV-17 already covers an unreadable ETA).
5) Stated justification (0.58.0 check): if the change explains its Impact level, no finding.
6) Messages (neutral, no question numbers):
   - count: "The Change Assessment says <quote, max 120 chars>; by the Impact definition
     that is <n> – <wording> (<definition text>). The change states <m> – <wording>.
     Confirm the Impact level, or explain why it is lower."
   - time: "<worst-case quote> with users restored in <time> suggests at least <n> –
     <wording>; the change states <m> – <wording>. Confirm the Impact level, or explain why
     it is lower."
   - when stated Impact is 4: add "Impact is still the Remedy default 4-Minor/Localized."
   - "How this was assessed": show the Impact definition table and the time bands; why
     advisory: "Impact is defined by how many users are affected; the restoration time is
     only an indication."
7) Tests (made-up fixtures): each count pattern and band; count beats time; time bands at
   1 h, 1 h 1 min, 2 h, 2 h 1 min; no time -> no finding; justification -> no finding;
   deferral sentence ignored; default-4 line; never Major; attestation text never read.
8) Docs (rules catalogue, user guide impact section incl. the definition), CHANGELOG 0.61.0,
   pyproject 0.61.0.

Verification: ruff; tests for changed modules; browser -k review. Report rule set old -> new
and live before/after counts (codes and counts only). Do not run --update-baseline or the
audit. No git. Do not read cr_core/config.py, cr_core/history/config.py or .env. Never delete
anything under work/history/. No heredocs (not even empty ones), python -c, python - or stdin
redirects. Delete work/cv18_v2_review.md at the end.