0.53.0 changes (baseline NOT updated). Verification: UI level — ruff, tests for the
changed modules, browser tests -k pending and -k review only. No full suite, no audit.

1) CV-18 severity: Major (-20) while awaiting approval; advisory once Scheduled/Closed
   (same lifecycle as CV-14/CV-15). Not for Standard/Latent/Emergency, Internal entries,
   history replay (unchanged). Keep the message.
2) When CV-18 fires, do not show the "Impact is <level>. Say why the change needs it, or
   use a lower level" advisory on that change. Test.
3) Pending list and Executive Summary: read the Work Detail View Access needed for CV-15
   and CV-18 in the list read, so the score on Pending equals the Review score for every
   change. Read-only; same Internal handling as the Review page (Internal text never
   used or shown). Keep it efficient (one batched query per list, not per change, if
   Remedy allows). Report Pending load time before/after for the live list.
4) Test: a change with CV-18 shows the same score and verdict on Pending and Review.
5) Measure (live, awaiting approval): CV-18 count; verdict changes (Ready -> Needs work,
   Needs work -> Blocked). Rule catalogue, user-guide and CHANGELOG updated.
Delete work/impact_live.txt. Report the rule set id. Then stop.


python scripts/check.py --update-baseline
python scripts/check.py --browser --audit
git status
git diff --stat
git add -A
git status
git commit -m "0.53.0: Change Assessment checks (CES CAB standard) and impact advisory" -m "- CV-14 (Major): no Change Assessment Work Detail
- CV-15 (Major): one finding naming each missing or unanswered CAB question by its own
  wording; deferral justification by position; attestation checked for presence only
- CV-16 (Minor): deferral answer not Y/N; CV-17 (advisory): ETA without a readable time
- CV-18 (advisory): Impact may be understated - Business Impact describes customer,
  client or business-function harm and restoration time suggests a higher Impact than
  stated; quotes the sentence; Review page only
- Scored while awaiting approval, advisory once Scheduled; Standard, Latent and Emergency
  out of scope; not checked in history replay; attestation text never shown
- Link from findings to the Change Assessment entry; headings bold as whole phrases;
  Technical-details checklist; Notes labels no longer split
- Exec Summary and Notes fixes name the questions instead of numbers or 'above'
- Pending layout tests measure width without the scrollbar; Copilot verification levels
- Rule set a281f7da -> <new id>; baseline, docs, CHANGELOG and tests updated"
git push