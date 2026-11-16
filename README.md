0.52.1 additions (same release; baseline still NOT updated).
Constraints unchanged: never read/search/print cr_core/config.py, cr_core/history/config.py
or .env; no Remedy writes; no crq login; no git; no inline Python (-c/stdin/heredoc) —
scripts in a file under work/, deleted after; do NOT run --update-baseline; history.db
schema unchanged, no people stored; chat shows codes and counts only — no change numbers,
names or note text. Delete work/livecheck_review.txt; keep work/execsummary_spotcheck.txt.

NOT changed (confirmed): MF-01 and MF-02 stay exactly as they are (Major/Please confirm
logic unchanged); the open-task scheduled dates rule; the Exec Summary rule.

A) Q-VAGUE-01 (Major) and Q-VAGUE-03 (Minor, impact answers): add the reason words and
   patterns from the simulation — hence, therefore, not used / not in use, no consumers,
   shadow mode, read-only — and the scoped form "no impact to <X>" when the same or the
   previous sentence states a possible impact (e.g. "temporary disruption is possible").
   A bare "No impact" with no reason stays flagged. Reason words live in config, not code.

B) Q-VAGUE-02 (vague wording): ignore "etc"/"etc." inside the Notes template's own
   bracketed text — "(Blue/green, Canary, etc)", "(Blue/green, Canary, etc.)",
   "(LG, CES CAB, HRCAB etc)", "(LG, CES CAB, HRCAB etc.)" — listed in config as template
   phrases. "etc" anywhere else in the owner's text is still flagged.

C) GEN-01 (release name): applies only to application deployments/releases (deployment,
   release, PCF/Harness/Blue-Green, artifact, build, package promotion, version words).
   Credential/password rotation, certificate renewal, index/DDL/data changes, patching and
   configuration-only changes are not asked for a release. Classification words in config.

D) Task links: label "View task n" when the Remedy sequence is unique; when shared,
   "View task n · k of m" (k = order within that sequence). Tooltip = task name. Link
   target unchanged. Same labels in CV-13 and every other finding that lists tasks.

TESTS: each reason word/pattern clears; bare "No impact" still Major; template-bracket
"etc" ignored while owner "etc" flagged; GEN-01 kept for a deployment with no version,
skipped for password rotation, cert renewal, DDL, patching, config; task labels for 9
tasks sharing sequence 1 -> "1 · 1 of 9" … "1 · 9 of 9". Existing tests stay green.
DOCS/CHANGELOG 0.52.1 (add to the existing entry). VERIFY: ruff, full suite,
check.py --browser --audit (report rule set id).

MEASURE (built code, same live scope): per rule before -> after (cleared / kept / added);
verdict changes (to Ready, Blocked -> Needs work, any worse). Add to
work/execsummary_spotcheck.txt: 10 GEN-01 changes classified "configuration" (now
skipped) and 5 classified "application deployment" (kept), each with change id and
Summary (<=100 chars), so I can confirm none is really a release. Then stop.