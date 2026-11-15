0.52.1 additions (same release; baseline still NOT updated). Usual constraints (no
config.py/.env, no Remedy writes, no crq login, no git, no inline Python, no
--update-baseline; codes/counts only — no change numbers, host names or note text).
Keep work/execsummary_spotcheck.txt.

A) INF-01 (hosts/CIs named)
   - Pass when Remedy relates at least one Configuration Item whose status is not
     Disposed or Delete (End of Life counts as related). Any relationship type.
   - Only when no such CI is related, keep the current text check (host/server words,
     host-name shape) in Summary and Notes.
   - When it still fires, never list CIs. Message: "No usable Configuration Item is
     related to the change, and the Summary and Notes name no host or server."

B) New advisory (0 points), e.g. INF-11 (next free id): "<n> related CIs are no longer
   in use (Disposed/Delete)." List them under Technical details only. Statuses come from
   relationships.status (already read). End of Life is not flagged.

C) INF-05 (certificate expiry, chain, endpoints)
   - Certificate sub-type only from the phrases "certificate renewal" or "ssl certificate";
     single words (certificate, cert, ssl, tls, csr) no longer set it on their own.
   - When operational categorization tier 1 is Patch, INF-05 is an advisory (0 points)
     instead of a Major. Elsewhere it stays Major.

TESTS: INF-01 passes with one Deployed CI and with one End of Life CI; fires (new message,
no CI list) with only Disposed/Delete CIs and no host words; text check still used when no
CI is related. INF-11: Disposed + Delete counted, End of Life ignored, 0 points.
INF-05: single word "tls" -> no certificate sub-type; phrase on Patch change -> advisory;
phrase on non-Patch change -> Major. Existing tests stay green.

DOCS: infrastructure rules doc / regenerated catalogue, user-guide if relevant,
CHANGELOG 0.52.1 (add to the existing entry). Version stays 0.52.1.
VERIFY: ruff; full suite; check.py --browser --audit (report the new rule set id).
MEASURE (built code, same live scope): INF-01 Majors before -> after; INF-11 advisories
(changes); INF-05 Majors -> advisories / removed; verdict changes caused by A-C (to Ready,
Blocked -> Needs work, any worse). Add 10 INF-01 cleared cases and 5 INF-05 cases to
work/execsummary_spotcheck.txt (rule id, CI count, statuses, categorization tier 1). Then stop.