READ-ONLY follow-up (temporary helper under work/, delete afterwards; no inline Python;
no rule/config/test changes; no git). Codes and counts only.

1) Do we read the task Status Reason field from Remedy today (task field map / history)?
   If not, give its field name/ID from the field map or docs, and say whether history.db
   stores it.
2) For REFERENCE tasks only (same name rules as the last run), counts of
   task Status × Status Reason (if available), split by the CHANGE's status group:
   - not started: Draft, Planning In Progress, Scheduled For Review, Scheduled For Approval,
     Scheduled
   - started/done: Implementation In Progress, Completed, Closed
   History and live separately.
3) Re-run the CC-05 measurement table with:
   - not-started changes: open reference tasks only (Closed ignored)
   - started/done changes: open + Closed reference tasks, excluding Status Reason values that
     mean cancelled (list which values you treated as cancelled)
   - Option B: a reference task ENTIRELY outside the change window is ignored for CC-05 and
     counted separately as "stale task" (would be a new Major)
   Report: Blocker / Advisory / fallback / stale-task counts, and Blocker→Advisory and new
   Blockers vs today.