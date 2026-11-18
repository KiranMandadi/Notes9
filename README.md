0.53.2: MF-01, MF-02 and GEN-01 also search tasks and the Change Assessment. Usual
constraints; no git; do NOT run --update-baseline. Verification: Quick level (ruff + tests
for the changed modules; browser tests -k review only for the "Searched:" link).

1) Sources, in addition to Summary and Notes:
   - task Summary (name) and task Notes of usable tasks: implementation tasks (current
     name rule) plus tasks whose name contains scheduler, job, batch, spr, control-m,
     deploy or install; exclude certification/rollback/backout/back out/pre-/post- tasks;
     same status rules as CC-05 (no Cancelled/Canceled/Bypassed).
   - Change Assessment answers "Deployment Strategy" and "Deployment Type" (Public entries
     only; never Q7).
   History replay: use task text only if history stores it; otherwise unchanged (say which).
2) Evidence: when matched in a task, the snippet links to that task ("Task 3 · Deploy
   ..."); when matched in the assessment, link "Work detail › Change Assessment". When not
   found: "Searched: Summary, Notes, Tasks and Change Assessment – not found".
3) Tests: LPAR in an implementation task name clears MF-01; Control-M + job names in a
   scheduler task clear MF-02; "v2.4.1" in a deploy task clears GEN-01; same text only in
   a rollback or certification task does NOT clear; cancelled task does NOT clear.
4) Measure (live, awaiting approval + scheduled): MF-01 / MF-02 / GEN-01 before -> after;
   which source cleared them (task / assessment); verdict changes; 0 new findings.
   Write work/sources_review.txt with up to 20 cleared cases: change id, rule, source,
   matched text (<=120 chars). Do not print it.
CHANGELOG 0.53.2; pyproject 0.53.2. Report rule set id. Then stop.