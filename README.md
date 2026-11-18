0.53.1: retire advisories CV-02, CV-03 and CV-08 (user feedback). Usual constraints; no
git; do NOT run --update-baseline. Verification: Quick level (ruff + tests for the changed
modules; browser tests -k rules and -k guide only if their text changes).

1) Remove CV-02 (top levels of Urgency/Impact/Priority justified), CV-03 (risk level 4 or
   5 confirmed) and CV-08 (required Work Details present) from the rule packs and any
   code/config used only by them (incl. the CV-18 -> CV-02 suppression). IDs not reused;
   list as retired in the rules catalogue and CHANGELOG 0.53.1 with the reason ("user
   feedback: duplicated by the Change Assessment checks and CV-18").
2) Update everything that mentions them: Rules page counts, Guide page (sample report,
   FAQ, glossary), user-guide, configuration, open items (e.g. D27), tests (remove only
   tests for the retired rules; list each).
3) Measure (live, awaiting approval + scheduled): how many changes showed each rule
   before; confirm 0 score/verdict changes.
4) pyproject 0.53.1. Report rule set id, files changed, test counts. Then stop.