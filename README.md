0.56.0 polish (UI only). UI level (browser tests -k pending and -k review only).
1) Decision tooltips: remove the keyboard letters. Not selected: "Approve" / "Put on hold"
   / "Needs work". Selected: "Approved · click to clear" / "On hold · click to clear" /
   "Needs work · click to clear". Shortcuts still work; mention A / H / N in the Guide's
   Pending section only.
2) Decision icons as one inline-SVG set (same size, stroke weight, rounded caps; no text
   glyphs or emoji): Approve = check mark (short + long stroke, clearly not a "v"), On hold
   = outline clock, Needs work = circular arrow. Colours unchanged (green / blue-grey /
   amber); selected = white icon on the filled colour. Use the set everywhere decisions
   appear: overlay buttons, Pending row, status messages, filter.
3) Copy decisions:
   - Heading: "Review decisions · <date>" (date only; no time, no approver, no name).
   - Summary line: "Approved n · On hold n · Needs work n · Not decided n" — remove the
     "(n awaiting approval)" part.
   - Column "Review Decision" renamed to "Decision"; other columns unchanged.
   - Rich format: Decision text coloured — Approved #1E6B45, On hold #3A5A80, Needs work
     #8A4B08 (semi-bold). Plain text unchanged apart from heading, summary, column name.
   - Keep grouping by decision (Approved, On hold, Needs work).
4) Delete work/ca_spotcheck.txt and work/sources_review.txt (they hold change numbers).
Tests: tooltip text; SVG icons rendered for all three decisions in row and overlay; Copy
decisions heading, summary, column name and colours. Then stop.