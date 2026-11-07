Small change on Pending: before the existing decision pill on the CRQ line, add a plain text label "Review:" (12 px, #5B6880, 4 px gap to the pill). Keep the pills unchanged ("✓ Approved" / "↻ Needs work", same outlined style). Add a tooltip on the label and pill: "Decided in this review meeting. Not recorded in Remedy." The label shows only when a decision exists. Same in the phone cards; calendar bar tooltips say "Review: Approved / Needs work". Update the tests and the CHANGELOG (no new version). Run the browser tests; report counts. No branches, tags or commits.

git status
git add -A
git commit -m "Pending: review decision on the CRQ line with Review label; Back to top on all long pages and the overlay; balanced report columns"
git push