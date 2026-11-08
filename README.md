Pending View by follow-ups + Copilot command rule. Same standing rules; no git operations unless I ask.

1. Value cards: remove the share bars. Every card (All tile included) has the same three lines, so heights match with no empty space:
   - Line 1: label (13 px, 500); white ✓ circle on the right when selected. Remove the % from the top-right.
   - Line 2: count (26 px, 600).
   - Line 3 (12 px): unselected "<pct>% of all" (#5B6880); selected "<pct>% of all · showing" (#C9D4E6 on navy); zero-count "None".
   - All tile line 3 unchanged ("Showing every change" / "Show all").
   Remove the bar colour tokens if nothing else uses them.

2. Add a "FILTERS" label at the left of the filter chip row, same style as "VIEW BY" (11 px, 600, caps, letter-spacing 0.7px, #5B6880). Both labels sit in a shared 76 px label column. The first filter chip, the first View by tab and the grey panel all start on the same left edge. Phone: labels sit above their row.

3. Go back to folder tabs for View by: the active tab has background #F1F4F8 and rounded top corners (10 px). Inactive tabs are plain text (#5B6880) with no background. Use no underline and no rule under the tab row. The tiles sit in a #F1F4F8 panel (14 px padding, 12 px radius; top-left corner 0 when the first tab is active).
   The active tab must join the panel seamlessly: no white gap, border or line between them (tab overlaps the panel by 1 px, no padding or margin between the tab row and the panel). Keep "Grouped by <dimension>" right-aligned on the tab row.

4. Remove the opacity fade on unselected value cards when a value is selected. Only zero-count cards are muted (0.45, not clickable). The selected card stays solid navy with ✓.

5. Review decisions bar must ignore View by, search and every other filter on the page: "Decided N of M" counts across all changes for the current approver scope (as loaded), Copy Decisions copies all recorded decisions, and Clear clears all. Example: 2 changes, 1 decided, View by ORR 4 – Very High selected → still "Decided 1 of 2".

6. Add this section to .github/copilot-instructions.md and follow it from now on, including for this task:
   ## Running commands
   - Never run inline Python (`python -c`, `python -` with heredocs, or `bash -c "python ..."`). Endpoint security flags these.
   - To run Python, use an existing entry point: `crq ...`, `pytest ...`, or `python scripts/<name>.py`. If a one-off helper is needed, ask first; if I agree, create it as a file under scripts/ and run that file.
   - Prefer the editor's search and file tools over shell commands for reading and searching files.

Check at 1440 and 1920 px on all four tabs, zooming in on the tab/panel join. Update the browser tests (add one for item 5: decide a change, filter it out, check the count and copied text) and screenshots; CHANGELOG (no new version). Run the browser tests with pytest; report counts.
No branches, tags or commits.

git status
git add -A
git commit -m "Pending: View by redesign (folder tabs, All tile, three-line cards), Filters label, decisions count ignores filters; Copilot command rule"
git push