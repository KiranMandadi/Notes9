Read-only research: which exception Work Detail types do changes in restricted periods
carry? Do not change any code, rule, config or baseline. No git.

Population: changes whose window overlaps any restricted (freeze) period in calendar.yaml:
- current/upcoming: NOV Month End Processing (27 Nov 09:00 – 2 Dec 09:00 ET);
- past: the three earlier restricted periods in calendar.yaml (26 Oct – 2 Nov, 4 – 8 Nov,
  13 – 15 Nov), read live from Remedy, read-only, any status.
Same class scope as the audit (exclude Standard, Latent, Emergency); report Emergency
separately as a count only.

For each change, read the Work Detail entry TYPES only (never the note text, never Internal
entries, no submitter names). Report counts per period and in total:
- Restriction Exception only
- Restriction Approval Notes only
- both Restriction Exception and Restriction Approval Notes
- Windows Exception (with or without the others)
- none of these
Also, if the "In Scope of Restriction" field can be read via the existing field map or a
read-only metadata query, cross-tab its value (Yes / No / blank) against the rows above.
For the current period, also give the CC-05 result (fired / cleared) and which type cleared it.

Write work/restriction_wd_review.md: change number, period, status, In Scope value (if
found), exception types present (type names only). I will delete it.
Codes and counts only in chat. Do not read cr_core/config.py, cr_core/history/config.py or
.env. Never delete anything under work/history/. Any heredoc, python -c or python - is a stop
condition. Then stop and report.