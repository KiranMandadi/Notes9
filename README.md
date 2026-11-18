0.54.0 polish (no rule changes). UI level (browser tests -k pending only). Keep the
current CRQ-line order and the "Review decision" label.
1) Decided rows: the filled icon is shown only on row hover/focus (same as the rest of
   the controls). At rest the row shows only the green / amber left edge. Touch
   (hover:none): controls always shown.
2) Undecided icons on hover: coloured outlines instead of grey — ✓ green (#1E6B45 on
   white, border #9CD3B5), ↻ amber (#8A4B08 on white, border #EBC58D); pale tint on button
   hover (#E3F4EA / #FDF0DC). Selected stays filled (green / amber, white icon).
3) Status message colour follows the decision: Approved -> green with ✓ (existing success
   style); Needs work -> amber with ↻ (tint #FDF0DC, bar #D97706, text #6B3A06); Cleared
   or Undo -> neutral grey with ○.
4) Decision filter as a real segmented control, styled like the List | Calendar toggle:
   label "Review decisions", then [All 6 | Not decided 4 | Decided 2] — grey track,
   selected option a raised white pill with bold text, hover tint on the others,
   role="radiogroup" with arrow-key support. Counts are for changes awaiting approval.
   Remove the separate "Decided N of M" text. Then "Copy decisions" and "Clear".
5) "Clear": confirm before clearing ("Clear N decisions? This cannot be undone.") or
   provide Undo in the status message.
Tests: no decision icon at rest on a decided row; shown on hover/focus; outline colours;
message colour per decision; segmented control counts and selection (mouse + arrows);
Clear asks (or Undo restores). Then stop.