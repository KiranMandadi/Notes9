0.56.0 polish (UI only; baseline NOT updated). UI level (browser tests -k pending and
-k review only). No heredocs, python -c or python - (stop and ask instead).

1) Decision tooltips (Pending row icons only — the overlay buttons have no tooltip, their
   labels already say it): no keyboard letters. Not selected: "Approve" / "Put on hold" /
   "Needs work". Selected: "Approved · click to clear" / "On hold · click to clear" /
   "Needs work · click to clear". Overlay buttons keep their aria-labels for screen
   readers. Shortcuts still work; mention A / H / N in the Guide's Pending section only.

2) Decision icons as one inline-SVG set (viewBox 24, 16px in rows / 17px in overlay
   buttons, round caps and joins; no text glyphs or emoji), as on the design board
   "Decision icons - Approve / On hold / Needs work":
   - Approve: bold check, path "M4.5 12.5l5 5L19.5 7", stroke-width 3.
   - On hold: clock, circle r=8.5 + hands "M12 7.5V12l3 2", stroke-width 2.2.
   - Needs work: pencil, "M15.5 4.5l4 4L9 19H5v-4z" + "M13.5 6.5l4 4", stroke-width 2.2.
   Colours unchanged (green / blue-grey / amber); selected = white icon on the filled
   colour. Use the set everywhere decisions appear: overlay buttons, Pending row, status
   messages, filter.

3) Copy decisions:
   - Heading: "Review decisions · <date>" (date only; no time, no approver, no name).
   - Summary line: "Approved n · On hold n · Needs work n · Not decided n" — remove the
     "(n awaiting approval)" part.
   - Column "Review Decision" renamed to "Decision"; other columns unchanged.
   - Rich format: Decision text coloured — Approved #1E6B45, On hold #3A5A80, Needs work
     #8A4B08 (semi-bold). Plain text unchanged apart from heading, summary, column name.
   - Keep grouping by decision (Approved, On hold, Needs work).

4) Pending row decision controls: after a mouse click, the row's controls hide when the
   pointer leaves (today they stay because the clicked button keeps focus). Show them on
   hover, or when the row contains keyboard focus (:focus-visible / :has(:focus-visible)),
   not on mouse focus. Decided rows at rest show only their coloured edge.

5) Delete work/ca_spotcheck.txt and work/sources_review.txt (they hold change numbers);
   leave work/history/ and work/accuracy-audit/ untouched.

Tests: row tooltip text (no letters) and no tooltip on overlay buttons; SVG icons for all
three decisions in row and overlay; click a decision on row 1, move pointer to row 2 ->
row 1 controls hidden, keyboard focus still shows them; Copy decisions heading, summary,
column name and colours. Report files and test counts. Then stop.