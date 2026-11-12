Pending: Refresh feedback, filter highlighting, Status values. Same standing rules; no git operations unless I ask. If you ask me something and get no answer, stop and wait. UI/filter logic only; rule set id unchanged — confirm it.

1. Refresh:
   - While refreshing: cursor: progress on the whole page (cleared when done, failed or cancelled); Refresh button shows a spinner + "Refreshing…" and is disabled; the current table stays visible until the new data arrives.
   - When done: update the "as of …" timestamp and flash it teal (#E8F3F2 background, fade over ~1 s).
   - After 8 s: "Still working — Remedy is slow to respond · Cancel" in the same place as for reports (Esc also cancels). On failure: "Couldn't refresh — Retry" there, keeping the old data on screen.

2. Filter chips: one rule — teal (border #9FD0CA, background #E8F3F2, value #0B5F59) whenever the filter narrows the list (not All/Any), whether it's a default or a user choice; white otherwise. Applies in both views:
   - My approvals default: ORR, Risk Level, Status, Class, Approver teal; Impact, Quality, Date, Organisation, Group white.
   - All approvers default: Status, Class teal; the rest white.
   - "×" on a chip only when the user changed it from the view default; clicking it resets that filter to its view default. Approver keeps its existing "×".
   - "Clear all" shown only when any filter differs from the current view's defaults.

3. Status filter: remove "Request For Authorization" and "Scheduled For Review" completely (popover, on-demand fetch, URL codes, labels, tests, docs). Remaining values, in order: Planning In Progress, Scheduled For Approval. Default unchanged: Scheduled For Approval. Planning In Progress keeps on-demand loading ("Loads when selected"). Labels: "Status Scheduled For Approval" (default), "Status Planning In Progress", "Status All stages" (both). Old URLs containing the removed codes (rfa, review) ignore them without error. Update docs/decisions.md with one line ("Status filter: Request For Authorization and Scheduled For Review removed — not used in the review meeting").

Tests: refresh sets/clears progress cursor, spinner text, disabled button, timestamp flash, slow message, failure keeps old data; chip colours in both views' defaults; × only on user-changed chips and resets to default; Clear all hidden at defaults and shown otherwise; Status shows only the two values, default label, "All stages" label, on-demand load of Planning In Progress, old rfa/review URL codes ignored. Run ruff, touched unit tests and browser tests -k "pending or filter". List decisions under "Decided"; one CHANGELOG line.
No branches, tags or commits.


git status
git add -A
git commit -m "Pending: Refresh progress feedback; highlight narrowing filters; Status limited to Planning In Progress and Scheduled For Approval"
git push