Final polish — Tasks, Work detail and report footer (0.50.0). UI only.

1) Tasks "#" column → header "Step", tooltip "Remedy task sequence — tasks with the same step
   run in parallel". Within the current sort by sequence, show the step number only on the first
   row of each same-step group; following rows show a faint vertical connector (1px #DDE3EC)
   instead of the number. When sorted by another column, show the number on every row.

2) Remove the "No dates" tag under the task name (the Scheduled column already says "No
   scheduled dates"). Keep the "Outside window" and "In freeze" tags. Keep "No dates" in the
   Needs attention count and in the Issue line.

3) Work detail rows on ONE line: Added shows "Fri 13 Nov · 18:11 (12 hours ago)" with the
   bracket part muted (#8592A8). Type, Added and Submitter vertically centred; row padding 10px.

4) Type filter popover:
   - "Select all" and "Clear" links at the top, the same as the Pending filters.
   - max-height 320px with an internal scroll; not clipped by the card (render above, z-index;
     flip upward if there's no room below).
   - full type names, never cut off; counts right-aligned.

5) Empty state when the filter matches nothing: centred muted text "No entries match the Type
   filter · Select all" (link resets the filter). Hide the column headers and the footer hint
   in that state.

6) Remove the footer line "The score rates the quality of the change record; it does not predict
   how the change will go." from the Console report and the saved HTML report. Add the same
   sentence as the tooltip (title/aria-describedby) on the score ring in the report header.
   Update any test that checks the footer text.

Check at 100% and 110% zoom. Run the Review browser tests and ruff only. Report files and
counts, then stop. No git.