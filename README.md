Pending table — one shared pill style for the Window column AND the Quality column, matching
the row status pill on the Window column's third line ("Scheduled", "Scheduled For Approval").
Colours stay exactly as they are.

1) Shared style, defined once (one CSS class or variable set) and used by all of them:
   font-size 11px, font-weight 600, line-height 16px, padding 2px 8px, border-radius 999px,
   same letter-spacing, same border (none or the same width), inline-flex, align-items center.
   Applies to:
   - Window column: Today, Tomorrow, any date/weekday tags, "Freeze · exception" and any other
     freeze/blackout tag, and the row status pill.
   - Quality column: Ready, Needs work, Blocked (the pill under the score).
   Keep each pill's current background and text colours.

2) Window second line (duration + pills): duration stays 13px; pills vertically centred with
   it; 6px gap; wraps cleanly when the column is narrow.

3) Quality column: score stays 14px/600; pill below it with the existing 4px gap; centring
   unchanged.

4) Status-line tick: the "Updated HH:MM · N changes" pill shows a "√" glyph. Use the same
   inline SVG check as the saved-views menu (12px, stroke 2, currentColor). Same for any other
   ✓ / ⚠ / ⓘ glyphs in the status pill.

Pending table and status pill only — don't change chips, the quality report, or other pages.
Check at 100% and 110% zoom. Run only the Pending browser tests covering the Window column,
Quality column and status pill; update any test that checks the old pill sizes. Report files
changed and counts, then stop. No git.