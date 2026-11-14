python scripts/check.py --update-baseline
git status
git diff --stat
git add -A
git status
git commit -m "0.49.0: freeze check (CC-05) based on implementation/certification tasks" -m "- CC-05 judges reference tasks (name contains implementation/certification; rollback/backout and pre/post-implementation excluded); falls back to the change window when no usable task
- Not-started changes count open tasks only; started/done changes also count Closed tasks unless Status Reason is Cancelled
- New CC-09 advisory: change window spans a freeze but no reference task inside it
- New CV-13 (Major): reference task entirely outside the change window (stale dates), excluded from CC-05
- CV-04 justification asked only when CC-05 finds a freeze hit; scope/type checks unchanged
- Task Status Reason read live (same request) and in history replay
- Freeze displays (At a glance, verdict line, Pending tag, calendar) follow CC-05
- Config in calendar.yaml (reference_tasks, closed_statuses); rule packs change-class 1.14.0, common-validation 4.5.0
- Measured: history CC-05 24->13, CC-09 11, CV-13 16; live CC-05 30->28, CC-09 2, CV-13 75; 0 new Blockers; audit 0 mismatches
- Rule set 7066972d; docs, catalogue, research note and tests updated"
git push


READ-ONLY check — no file changes, no git, no inline Python. Don't read cr_core/config.py,
cr_core/history/config.py or .env. Codes and counts only; do not print any task or work-info
content, people's names or change numbers.

We plan two Review-page panels: Tasks and Work detail. For each field below, report in one
table: | Panel | Field we need | Remedy form + field name (and field ID if known) | Already in
remedy_field_map.yaml? (key name) | Already fetched in the live query today? | Needs adding? |
Notes |

TASKS (TMS:Task)
- task ID, sequence, name, status, status reason (being added in the CC-05 work — just note
  it), assigned group, task type (Manual/Automatic), scheduled start, scheduled end,
  summary, notes/description

WORK DETAIL (CHG:WorkLog or the form we use for Work Info)
- work info type, summary (Description), notes (Detailed Description), submit date,
  submitter, source, view access (Internal/Public), attachment names, attachment sizes
  (names/sizes only — no download), number of attachments

Also answer:
1) Is Work Info read today at all? (CC-05 exceptions use work-info types — which query, which
   fields?) Can the extra fields come from the SAME request, or is a new query needed?
2) Are attachment names/sizes available without downloading the attachment itself? Which
   fields?
3) Are task and work-info rows bounded/paged today (max rows)? What happens with 100+
   work-info entries?
4) Any field that is restricted or likely to be empty in our Remedy (e.g. summary not used)?
   Check with a COUNT of non-empty values over a sample of live changes, counts only.
5) Do mock data (remedy/mock.py) and the history replay need these fields? (History: no —
   panels are live only. Confirm nothing in history.db changes.)