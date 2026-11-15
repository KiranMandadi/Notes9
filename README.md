Window fields discovery. Read-only. No code, config, rule or history-schema changes.
Do not read cr_core/config.py, cr_core/history/config.py or .env. No writes to Remedy.

1) Field map: check remedy_field_map.yaml for these Change (Date/System tab, "Window
   Exception" section) fields: Approved Implementation Window, Type of Window, Platform,
   Specialized Windows, Timing Reason. Report which exist (field ids) and which are missing.
   For missing ones, find the field ids read-only from the form metadata via the existing
   client, without adding them to the map.

2) History: report whether history.db holds any of these fields. If yes, count by value over
   all history: Type of Window; Platform; Platform x Specialized Windows; Approved
   Implementation Window; Timing Reason. Also count blanks.

3) Live (if history lacks them): read-only query of changes with Scheduled Start in the last
   90 days and next 30 days, production and non-production, all classes. Same counts as (2),
   split by class (Normal / Expedited / Standard / Emergency) and by Status group
   (not started / in progress / closed).

4) List the full menu values Remedy offers for Platform, Specialized Windows (per Platform if
   dependent), Approved Implementation Window and Timing Reason.

Output in chat: field ids, menu values and counts only. No change numbers, names or
summaries. Put any per-change working list in work/windows_discovery.txt and delete it
when done. Scripts go in a file under work/, no inline Python; delete after. Then stop.