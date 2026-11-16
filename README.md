python scripts/check.py --update-baseline
python scripts/check.py --browser --audit


git status
git diff --stat
git add -A
git status
git commit -m "0.52.1: accuracy fixes across window, Exec Summary, CI, template, wording and release rules" -m "- Exec Summary: shortened question 2 recognised; fallback heading match only inside the
  block; missing vs unanswered named; one labelled highlight per question
- CC-06 window length: advisory (0 points); skipped when the window check passes, on
  24x7/multi-day Specialized windows, with a recorded exception or a stated reason
- CV-13: one header line, one line and one View task link per stale task
- INF-01: passes when Remedy relates a CI in use (not Disposed/Delete); INF-08 (new
  advisory): related CIs no longer in use
- INF-05: certificate only from 'certificate renewal'/'ssl certificate'; advisory on Patch
- CC-04: reads Remedy's Template+ field; SCT text search removed; Template in At a glance
- Verdict line names a freeze clash only with a CC-05 finding; rule panel has no Owner row
- CV-08 not applied to Standard changes
- No impact (Q-VAGUE-01/03): more stated reasons recognised; bare 'No impact' still flagged
- Vague 'etc' (Q-VAGUE-02): template's own bracketed wording ignored
- Release name (GEN-01): application deployments and releases only, incl. PCF/Harness/
  Blue-Green/artifact/build/promotion/version wording
- Task links: unique labels when parallel tasks share a step ('View task 1 - 2 of 9')
- Unchanged by decision: MF-01/MF-02, open-task scheduled dates, Exec Summary scope
- Rule set d1a893eb -> a281f7da; baseline, docs, CHANGELOG and tests updated"
git push