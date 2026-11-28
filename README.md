Also in 0.62.0: CV-17 (ETA with no readable time).
Treat "Roll Back (Backout) Type and ETA" and "User Restoration ETA" as answered, with no
finding, when the answer states there is nothing to roll back or restore: N/A, NA, not
applicable, none, not needed, no users, no user impact, no rollback needed (case-insensitive,
with or without a reason after it). Placeholders such as TBD, TBA, ASAP, "-", [todo] still
give the finding. CV-18 behaviour is unchanged (no readable time -> no time suggestion).
Update "How to meet it" to: give a time in minutes or hours ("15 min", "2 hours"), or say
"N/A" with the reason when there are no users to restore.
Tests: "N/A as the application has no users" -> no finding; "Not applicable" -> no finding;
"TBD" -> finding; "GitHub Actions; 5 minutes" -> no finding. Report CV-17 live count
before -> after (all pages, codes and counts only).