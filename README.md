Failure messages: show the reason in the visible text, not only on hover. Same standing rules; no git operations unless I ask. UI only.
- Not found: "CRQ000000012345 wasn't found in Remedy — check the number" (no Retry).
- Sign-in/permission: "Remedy sign-in failed — check the Console's Remedy account" (no Retry).
- Timeout/server/other: "Couldn't open CRQ… — Remedy didn't respond · Retry".
Same places as today (landing under the button, Pending on the decisions-bar line, overlay toolbar). Keep the full technical reason as the tooltip.
Tests (UI tier): each failure type shows its visible text and Retry only where listed. Run ruff and browser tests -k "review or pending or overlay". One CHANGELOG line.
No branches, tags or commits.

   git status
   git add -A
   git commit -m "Open reports in place with progress cursor; clear failure messages; table text and alignment fixes"
   git push