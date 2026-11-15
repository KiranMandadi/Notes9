Exec Summary rule: diagnosis and measurement only. Read-only; no code/config/rule/
baseline changes; usual constraints (no config.py/.env, no Remedy writes, no git, scripts
under work/ deleted after; chat shows codes, counts and question numbers only, no change
numbers, names or note text).

1) Explain how the Exec Summary rule finds each of the three questions (exact text, regex,
   numbering, key words?) and how the "standard template wording" advisory finds them.
   Why can the Major say "question 2 unanswered" while the advisory recognises a shortened
   question 2 on the same change? Show the matching code paths (file/function names).
2) Explain how the evidence snippet/highlight for the wording advisory chooses its
   location, and why it can land on a different question (e.g. 3 or 1) than the one
   reworded.
3) Measure on live changes (profile groups, Scheduled For Approval and later, plus
   history if notes are stored): Exec Summary findings by question number and type
   (missing / unanswered / reworded). Then simulate: question found by number + key
   words (Q1: changing, why; Q2: production impact, control; Q3: exceptional, recovery,
   risk) with non-empty text before the next question. How many current Majors would
   clear? Any new Majors? How many become wording advisories?
4) Write work/execsummary_review.txt with 20 cleared cases (question number, the heading
   as written, answer length) for my review. Do not print it in chat.
Propose the fix (matching and highlight), then stop.