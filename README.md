Pending: redesign the View by area (mock-up "Pending - View by options", option A). Same standing rules; no git operations unless I ask.
1. Tabs: replace the folder tabs and the grey panel with a plain underline tab row on the white filter card: "VIEW BY" label (11 px caps, #5B6880), then Operational Risk Rating (ORR) · Risk Level · Impact · Quality. Active tab: #0B1B33, 600, 2 px navy underline; others #5B6880, 400. 1 px #E6EBF2 rule under the row. Keep "Grouped by <dimension>" right-aligned on the same row, unchanged.
2. All tile (first, 196 px): label "All changes", total count (26 px, 600).
   - Active (default, no value picked): background #0B1B33, white text, white ✓ circle top-right, sub-line "Showing every change" (#C9D4E6).
   - Inactive (a value is picked): white, 1 px #DDE3EC border, navy text, sub-line "Show all" (teal #0E7C74, underlined). Clicking the tile clears the selection.
   Then a 1 px #E6EBF2 vertical divider.
3. Value cards (172 px fixed, left-aligned, 12 px gap, wrap):
   - Unselected: white, 1 px #DDE3EC border, label (13 px, 500) with % right, count (26 px, 600), 4 px share bar (track #EEF1F6).
   - Selected: background #0B1B33, white label and count, white ✓ top-right, share bar replaced by "<pct>% of <total> · showing" (#C9D4E6). While a value is selected, other cards go to opacity 0.6. Clicking the selected card again clears it.
   - Zero-count: opacity 0.45, not clickable (as today).
   - Share bar colours: ORR, Risk Level, Impact use navy shades by level, highest first: #0B1B33, #3A5280, #7F93B8, #C3CEE0. Quality uses Blocked #C2410C, Needs work #D9A23A, Ready #2F8A5B. Remove the old coloured dots.
4. Switching tabs clears the selection. URL parameters and filtering logic unchanged.
5. Results line: when a value is selected, "Showing N of M · <dimension short name> <value>", e.g. "Showing 11 of 30 · ORR 3 – High".
6. Accessibility: tile and cards are buttons with aria-pressed; visible focus ring; Enter/Space toggles.
7. Phone: tiles wrap two per row; the divider hides.
Check at 1440 and 1920 px, with 2 and 30 changes, on all four tabs. Update the browser tests and screenshots; CHANGELOG (no new version). Run the browser tests; report counts.
No branches, tags or commits.