Polish for the Tasks and Work detail rows (0.50.0). UI only; no data or rule changes.

1) Highlight from "View task" / "View work detail": the amber or navy left bar and tint fade out
   after about 2 s (transition 600 ms) and are removed when the row is collapsed.

2) Cancelled, bypassed and closed-cancelled tasks: in the Scheduled column, show a grey "—"
   instead of the amber "No scheduled dates", and no "No dates" tag. These tasks never run.

3) Rows in Full change details (Tasks, Work detail and the others): the right-hand description
   and the pills are centred vertically with the row title (align-items: center; one line).

4) The controls bar inside Tasks and inside Work detail is ONE row, centred vertically:
   - Tasks: left "Show: All · N / Needs attention · N"; right the expand button.
   - Work detail: left "Showing X of N" + Type chip; right the expand button.

5) In an expanded task, the problem line becomes a grid row with the label "Issue" and amber
   text, aligned with Task ID, Type and the rest.

6) Work detail columns: Type minmax(0,1fr); Added 220px; Submitter 260px; the chevron column
   stays fixed. All cells top-aligned to the first text line, so Type, Added and Submitter
   line up.

7) In an expanded entry (task or work detail), hide any label whose value is empty
   (no "—" rows).

8) Rename the inner buttons to "Expand all tasks" / "Collapse all tasks" and
   "Expand all entries" / "Collapse all entries". "Expand all" in Full change details stays as
   it is.

9) Work detail expanded entry: remove the Source and View access rows. Show only Summary (when
   it differs from the start of the notes), Notes, Attachments.

10) Notes formatting (task notes AND work-detail notes) — display only, never change wording:
   - keep existing line breaks
   - lines/runs of 5+ of * - = _ become a thin divider (1px #E6EBF2, 8px margin), not shown as
     text
   - insert a line break before list markers at word boundaries: "1." "2)" "Step 3" "•" and
     " - " at item start
   - insert a line break before inline labels of the form "Word(s) :" or "Word(s):" (up to 4
     words, Title Case or ALL CAPS) when preceded by sentence text; render the label semi-bold
   - URLs: plain text (NOT clickable), small mono font, middle-ellipsis when longer than 60
     chars, full URL in a tooltip; always wrap
   - collapse repeated spaces
   - the 5-line clamp and Show more apply AFTER formatting
   Do the formatting in one small, pure function with unit tests (examples: run-on text with
   "Team :" labels, ***** separators, numbered steps, long GitHub URLs, text with no markers
   stays unchanged). Render as text nodes only — never innerHTML.

Check at 100% and 110% zoom. Run the Review browser tests, the new formatter tests and ruff only.
Report files changed and counts, then stop. No git.