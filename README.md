Read-only profile of the Pending list (no code changes). Live, Status = Planning In Progress,
Class = All except Standard (today about 571 changes). Report codes and counts only:
- total time, split into: search pages, per-change related reads (by form: tasks, work
  detail, relationships, ...), scoring, rendering;
- number of Remedy requests in total and per change;
- how many changes are read and scored but then hidden by a filter (Class, Date, other), and
  which filters are applied after loading instead of in the Remedy search;
- current parallelism for related reads, and whether pages are scored before the next page
  is requested.
Then propose, with an estimated time for each: (a) moving filters into the Remedy search,
(b) reading the next page while scoring the current one, (c) showing rows as each page is
scored, (d) a safe increase in parallel reads. Stop and report; no changes.
No git, no baseline. Usual rules: no heredocs, python -c, python - or stdin; do not read the
config files or .env; never delete anything under work/history/; delete temp files in work/.