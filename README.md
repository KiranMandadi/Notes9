Read-only check: is the baseline current after 0.57.1?

1) Report the current rule set ID (the same way check.py computes it) and the rule set ID
   stored in the baseline. Say whether they match.
2) Run python check.py --audit (no --browser). Report pass/fail counts and any failure
   names. The known first-open browser test is not part of this run.
3) If they do not match, list which files feed the rule set ID and which of them changed
   since the 0.57.0 commit (git diff --name-only <0.57.0 commit>..HEAD is allowed, read-only).

Do NOT run --update-baseline. Do NOT edit, stage, commit or push anything. Do not read
cr_core/config.py, cr_core/history/config.py or .env. Codes and counts only in chat.
Any heredoc, python -c or python - is a stop condition. Then stop and report.