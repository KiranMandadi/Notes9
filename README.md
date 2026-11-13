Approver filter across statuses; generic Pending labels; row status pill. Same standing rules from .github/copilot-instructions.md; no git operations unless I ask. If you ask me something and get no answer, stop and wait. Exclude cr_core/config.py and cr_core/history/config.py from every search; summarise tracebacks instead of printing them. UI/query logic only; rule set id unchanged — confirm it.

Problem: Status = Scheduled with Approver = Rama Bokka shows 0 changes, although rama.bokka approved several of them; the Approver filter only matches Pending signatures.

1. Diagnose first (report, then fix): how the Approver filter is applied today (Remedy query vs local filter) and which signature fields/status values it uses.

2. Make approver matching data-driven: a per-status setting (in the profile config next to the Status filter list) saying how the approver is matched — "pending" (signature for this approver with status Pending) or "approved" (signature Approved by this approver). Set: Planning In Progress = pending, Scheduled For Approval = pending, Scheduled = approved. Each change is matched by its own status's rule; results from several statuses are combined into one list. Adding a status later must need only a config entry. Live data only; batch queries under the existing URL limit.

3. Generic labels: header eyebrow always "CHANGES" (replace "PENDING APPROVAL" everywhere, incl. the sticky header); headline unchanged ("<Name> · N changes" / "All approvers · N changes"). Empty state: "No changes match the filters." + "Clear search and filters". No status-specific wording anywhere.

4. Row status pill: when more than one status is selected, show the change's Remedy status as a small grey pill (same style as "Freeze · exception") on its own third line in the Window column, under the duration/tags line; also in the calendar tooltip. Hidden when exactly one status is selected. Keep cells top-aligned; the row must not grow taller than the Change column's three lines.

5. Review decisions, hidden-changes pill, calendar and Copy Decisions follow the result as today.

Tests (Remedy mocked): Scheduled + approver who approved → listed; Scheduled + approver not on it → not listed; Scheduled For Approval behaviour unchanged; mixed statuses combine correctly; a new status added via config only works; "CHANGES" eyebrow and sticky header; generic empty state; status pill shown only with 2+ statuses, on the Window column's third line. Run ruff, unit tests and browser tests -k "pending or filter or calendar". One CHANGELOG line; user-guide (Approver filter, status pill).
No branches, tags or commits.

git status
git add -A
git commit -m "Pending: approver matching per status (approved for Scheduled), generic CHANGES labels, row status pill"
git push