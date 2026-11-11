Pending: replace View by with ORR / Risk Level / Impact / Quality filters (mock-up "Pending - filters without View by", layout B "By meaning"). Same standing rules from .github/copilot-instructions.md; no git operations unless I ask. If you ask me something and get no answer, stop and wait. UI/filter logic only; rule set id unchanged — confirm it.

1. Remove the View by area entirely (tabs, All tile, value cards, tray, "Grouped by"). Table sort stays ORR, then risk, then start time.
2. Filter card, two labelled rows (labels in the existing 76–92 px label column, same style as today's "FILTERS"):
   - RISK: ORR · Risk Level · Impact · Quality
   - SCOPE: Status · Class · Date · Organisation · Group · Approver · Clear all (right)
   1 px #EEF1F6 rule between rows. Same chip and popover component as Class/Status (Select all / Clear / Only / Default where it has a default, counts, zero-count values tucked under "Show N with no changes", Done, Esc restores, full labels, no ellipsis).
3. New filters and values:
   - ORR: 4 – Very High, 3 – High, 2 – Medium, 1 – Low, Not assessed.
   - Risk Level: Risk Level 5 … Risk Level 1 (field 1000000180).
   - Impact: 1 – Extensive … 4 – Minor (same wording as the table).
   - Quality: Blocked, Needs work, Ready.
   Labels: "All" when everything with changes is ticked; the value names when 1–2 ticked (Risk Level as "Risk Level 5, 4, 3"); otherwise "N selected".
4. Defaults depend on the view:
   - My approvals (default approver set): ORR = 4 – Very High + 3 – High; Risk Level = 5, 4, 3; Impact All; Quality All; Class All except Standard; Status Scheduled For Approval.
   - All approvers ("Show all approvers" or removing the Approver): ORR All; Risk Level All; others as above.
   - "Show my approvals" returns to the my-approvals defaults.
   - Clear all resets every filter to the defaults of the current view (my approvals keeps the approver; all approvers keeps All approvers). Search text is cleared too.
   - Chip style: white when at its view default or All; teal only when narrowed beyond the default.
5. Hidden-changes pill: on its own line above the table card, left-aligned (the Review decisions bar stays on the right of the same line). Shown only when filters hide changes: "Showing N of M · K hidden by <filter names> filter(s) · Show all M". M = changes for the current approver scope at the selected Status, before Class/ORR/Risk Level/Impact/Quality/Date/Organisation/Group/search; name only the filters actually hiding changes. "Show all M" sets those filters to All. Style: background #FDF0DC, border #F1D3A1, text #6B3A06, "Showing N of M" bold, link #0E7C74 underlined. Headline shows the total: "<Name> · M changes" / "All approvers · M changes".
6. URL: new parameters orr, risk, impact, quality (comma lists of short codes); none when at the view default; remove the old view-by parameters, and old view-by URLs open the page with defaults (no error). Approver and search text never in the URL.
7. Calendar and Review decisions bar follow the same filters. Copy Decisions unchanged.
8. Phone: rows stack; the pill wraps.
Tests (UI tier + filter logic): defaults in both views; Show all approvers / Show my approvals; Clear all per view; each new filter narrows the table; labels; pill text, filter names, hidden count and "Show all" link; URL round-trip and old view-by URLs; calendar follows filters. Run ruff, unit tests for touched modules, and the Pending browser tests (-k pending or filter or calendar). List decisions under "Decided"; one CHANGELOG line (no new version).
No branches, tags or commits.