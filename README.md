Read-only measurement, Change Assessment template wording. No code, config, rule or
baseline changes. No git. Live, all pages, Change Assessment scope as today.
Match rule: a question heading matches the template when, after ignoring numbering (1., 4A.,
Q4), case, whitespace, punctuation, bold markers and a bracketed "(Y/N)", its words are
exactly the template's. Anything else is reworded.
Report codes and counts only:
- changes with at least one reworded question; distribution by count (1, 2, 3+);
- per template question: how many changes reworded it, and the 5 most common rewordings
  (heading text only);
- changes with questions missing entirely (not just reworded);
- impact if reworded = unanswered (option A): CV-15 counts and verdicts before -> after;
- impact if one Minor per change (option B): score and verdict changes.
Write work/ca_wording_review.md (change number, template question, heading as written).
Never the attestation answer, no names. I will delete it. Usual rules: no heredocs,
python -c, python - or stdin; do not read the config files or .env; never delete anything
under work/history/. Stop and report.