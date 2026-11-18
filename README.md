0.53.2 fix before commit (baseline NOT updated). Quick level.
GEN-01: the two task clears matched "...install the artifact into PRODUCTION". Show the
exact token that satisfied the rule on CRQ000002490660 and CRQ000002490822 (rule terms
only, no other text). The release must be an identifier, not a generic word: a version
pattern (v1.2, 1.2.3, release 5, R26.11), a build/run number ("build 1534", "#1534"), an
image tag (name:tag) or an artifact file/package name with a version (e.g. xyz-2.3.0.jar,
.war, .zip, .tgz, .nupkg). The bare words artifact, build, release, version, package, tag
do not count. Apply to all sources (Summary, Notes, tasks, assessment).
Tests: "install the artifact into PRODUCTION" -> not satisfied; "deploy darc-2.3.0.jar"
and "image svc:1.4.2" -> satisfied. Measure GEN-01 live before -> after (any new findings
are expected only where no identifier exists; list count). Update sources_review.txt.
Report rule set id. Then stop.

python scripts/check.py --update-baseline
python scripts/check.py --browser --audit
git status
git add -A
git status
git commit -m "0.53.2: retire CV-02/03/08; MF-01, MF-02, GEN-01 also search tasks" -m "- Retired advisories CV-02, CV-03, CV-08 (user feedback; covered by CV-14/15/18)
- MF-01, MF-02 and GEN-01 also search implementation and scheduler/batch tasks (name and
  notes) and the Change Assessment deployment answers; rollback, certification,
  pre/post and cancelled tasks excluded; Pending reads task notes so scores match Review
- GEN-01 requires a release identifier (version, build number, image tag or versioned
  artifact); bare words like 'artifact' no longer count
- 'Searched:' lists every source; cleared findings link to the task
- Rule set e5db8b35 -> <new id>; baseline, docs, CHANGELOG and tests updated"
git push