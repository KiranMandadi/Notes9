Pending CRQ line polish. Same standing rules; no git operations unless I ask.

1. "✓ Viewed": plain text instead of a pill — 12 px, #5B6880, no background or border.
2. Decision: one outlined pill with the icon first and the label inside: "✓ Review: Approved" / "↻ Review: Needs work". Inside the pill, "Review:" is weight 500 and the value weight 600; same outlined colours as now (Approved border #7CC4A0, text #1E6B45; Needs work border #E8B266, text #8A4B08); 12 px.
3. Remove the separate "Review:" label added in the last change. Keep the muted "·" separator only when both Viewed and a decision show. Tooltip on the pill: "Decided in this review meeting. Not recorded in Remedy."
4. Same in the phone cards; calendar tooltips say "Review: Approved / Needs work". Overlay buttons and Copy Decisions unchanged.
5. Update the tests and the CHANGELOG (no new version). Run the browser tests; report counts.

No branches, tags or commits.

git status
git add -A
git commit -m "Pending: review decision pill on the CRQ line, Viewed as plain text; Back to top on long pages and the overlay; balanced report columns"
git push