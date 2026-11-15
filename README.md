Exec Summary fix: build. Approved: your points 1-6, with point 4 applied to BOTH labels and
the new fallback heading (only inside the Exec Summary block: after the "Exec Summary"
heading and before the first Notes-template question / "DO NOT REMOVE" block).
Rules: Q-COMPLETE-10/-12 Major only when a question is truly missing or has no answer;
Q-COMPLETE-11 advisory names the question numbers; evidence and highlights one per
reworded question, in question order, each labelled "Question n". Neutral wording.
Usual constraints (no config.py/.env, no Remedy writes, no git, no inline Python, no
--update-baseline; codes/counts only in chat).
Tests: shortened Q2 ("How will production impact be controlled?") found and answered;
stray "Production impact:" / "Change:" line outside the block ignored; missing vs
unanswered messages; several reworded questions -> one advisory naming all, highlights
in order; existing tests stay green.
Docs and CHANGELOG 0.52.1; pyproject 0.52.1.
Verify: ruff, full tests, check.py --browser --audit (report new rule set id).
Measure with the built code on the same scope: Majors cleared / added, advisories
before -> after. Write work/execsummary_spotcheck.txt with every cleared Major and 10
cleared advisories (question number, heading as written, answer length). Delete
work/execsummary_review.txt. Then stop.