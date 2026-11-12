Landing error messages polish. Same standing rules; no git operations unless I ask. UI only; rule set id unchanged.
1. Not found and sign-in failures: show the message in the input's status line, replacing the "✓ CRQ…" line. Text #A61B1B (red); input border #C2410C. Remove the separate message under the button for these two cases. No Retry.
2. Editing the number clears the error and restores the normal status line and border.
3. Timeout/server errors: keep the message under the button, text #8A4B08 (amber), with the teal "Retry" link.
Tests (UI tier): not-found replaces the ✓ line in red with a red border; sign-in failure the same; editing clears both; timeout shows the amber message with Retry under the button. Run ruff and browser tests -k review. One CHANGELOG line.
No branches, tags or commits.

git status
git add -A
git commit -m "Open reports in place with progress cursor; clear, colour-coded failure messages; table text size and alignment fixes"
git push