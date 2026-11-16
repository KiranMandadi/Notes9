0.52.1 additions (same release; baseline still NOT updated).
Constraints unchanged: never read/search/print cr_core/config.py, cr_core/history/config.py
or .env; no Remedy writes; no crq login; no git; no inline Python (-c/stdin/heredoc) —
scripts in a file under work/, deleted after; do NOT run --update-baseline; history.db
schema unchanged, no people stored; chat shows codes and counts only — no change numbers,
names or note text. Keep work/execsummary_spotcheck.txt.

A) CC-04 (Standard change uses an approved template)
   - Source of truth: the Change form's "Template+" field (the template name, e.g.
     "Control-M: New Connection Profiles"). Find its field id read-only, add it to
     remedy_field_map.yaml, read it live with the change.
   - Pass when Template+ is non-empty. Major when a Standard change has Template+ empty.
   - Remove the SCT-number search in Summary/Notes/Relationships entirely. Message:
     "Standard change has no template selected (Template+ is empty)."
   - History replay without the field -> rule not applicable (no finding).
   - Show the template name in At a glance (Change section, row "Template").

B) Platform detection: use the Template+ name as one more input to classify(), alongside
   the categorization and text (e.g. "Control-M: ..." -> Control-M). Measure how many
   changes move from "Not identified" to a platform and which rules newly apply. If this
   adds any Major, list rule ids and counts and keep B out of the build until I confirm.

C) Verdict line "freeze clash, exception recorded": explain where this text comes from and
   when it is shown. It appears on unrelated changes, so check whether it is shown without
   a CC-05 freeze finding plus a recorded exception on that change. If so, show it only
   when both are true. Report counts before/after.

D) Rule detail panel on the Review page: remove the "Owner" row, as already done on the
   Rules page.

E) Measure only, no change: CV-08 (missing Work Detail types) on Standard changes — number
   of changes, and the missing types ranked by count.

TESTS
   - CC-04: passes with Template+ filled and no SCT text; fires with Template+ empty even
     when the text mentions an SCT number; history without the field -> no finding.
   - Platform detected from the template name.
   - Verdict line shown only with a freeze finding plus a recorded exception.
   - Rule panel has no Owner row.
   - Existing tests stay green; do not weaken any.

DOCS: rules docs / regenerated catalogue, user-guide if relevant, CHANGELOG 0.52.1 (add to
the existing entry). Version stays 0.52.1.

VERIFY: ruff; full test suite; scripts/check.py --browser --audit (0 mismatches apart from
the expected baseline step; report the new rule set id).

MEASURE (built code, same live scope: profile groups, Scheduled Start 2026-08-17 to
2026-12-15, Cancelled/Rejected skipped):
   - CC-04 Majors before -> after; Standard changes with Template+ empty.
   - Verdict changes caused by this round (to Ready, Blocked -> Needs work, any worse).
   - B, C and E counts as above.
   - Add 10 cleared CC-04 cases to work/execsummary_spotcheck.txt (rule, class, template
     present yes/no).
Report files changed, test counts, audit result, rule set id and the measurement; then stop.