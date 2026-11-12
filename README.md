python scripts/check.py --update-baseline
python scripts/check.py
git status
git add -A
git commit -m "Rules: revised freeze windows, Risk Level 4–5 Notes questions, Exec Summary check, CV-02 advisory"
git push

Q-COMPLETE-10: accept labelled Exec Summary sections as answers. Same standing rules; no git operations unless I ask. If you ask me something and get no answer, stop and wait. Never read or print cr_core/config.py or cr_core/history/config.py (exclude them from every search; summarise tracebacks instead of printing them). Do not run --update-baseline; I will.

Proposed: in addition to the three questions (exact or shortened wording), accept a labelled heading at the start of a line followed by ":" as the question, with its answer being the text after it up to the next heading:
- Q1: "Change", "What is changing", "Change description"
- Q2: "Production Impact Mitigation", "Impact Mitigation", "Production impact"
- Q3: "Exceptional recovery risk", "Recovery risk" (allow trailing words such as "associated")
Answers still fail if blank, N/A, NA, "-", TBD, None or template-only text. When labels are used instead of the standard questions, show the existing Q-COMPLETE-11 advisory (0 points). A paragraph with no recognisable labels, or any of the three missing, stays the Major.

Step 1 — measure only, then STOP: on the 130 saved pending changes (work/measure-rules/), report how many Q-COMPLETE-10 Majors would be removed, and quote each removed case (change number and the three matched label lines with the first ~80 characters of each answer), including CRQ000002487028. Also confirm no label matched inside ordinary sentences (show any match not at the start of a line).
Step 2 — after my OK: apply, bump the pack version, add unit tests (labelled form passes; labelled form with an empty or N/A section fails; unlabelled paragraph fails; label words mid-sentence don't match), run python scripts/check.py --browser --audit and pytest, and report the old/new rule set id, mismatches and score/status changes. One CHANGELOG line.
No branches, tags or commits.