Read-only research. Do not change any code, rule, config or baseline. No git.

Find the rule behind the "Please confirm: we could not find the LPAR, region or subsystem
affected…" finding. Report: rule ID, pack, severity, what classifies a change as mainframe
(each signal: title keyword, product, CI, platform field…), and exactly what text satisfies it.

On live data (same scope as the audit), report codes and counts only:
- how many changes are classified mainframe, and by which signal;
- how many get this finding;
- for those, a breakdown by kind of change, inferred from summary/tasks: Control-M or batch
  scheduling, Db2 (bind/DDL/data), CICS online, IMS, ChangeMan/code promotion, other;
- how many of them name something the check doesn't accept but that identifies where the
  change lands (job names, scheduler table/folder, Db2 subsystem ID, system or plex name).

Write a review list to work/mf_lpar_review.md (change number, signal that made it mainframe,
inferred kind, the identifier-like text found, max 160 chars, from Summary/Notes/Tasks/Change
Assessment only; never the attestation answer, never Internal notes, no names). I will delete it.

Do not read cr_core/config.py, cr_core/history/config.py or .env. Never delete anything under
work/history/. Any heredoc, python -c or python - is a stop condition. Then stop and report.