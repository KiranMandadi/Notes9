"Remedy" link label. Same standing rules; no git operations unless I ask. UI only; rule set id unchanged — confirm it.
1. Report header (page and overlay): change the link text "Open in Remedy ↗" to "Remedy ↗". Colour, size, title, target and rel unchanged.
2. Pending list: replace the lone ↗ icon with the text "Remedy ↗" (13 px, 600, #0E7C74, underlined on hover), after the copy icon. Still shown only on row hover/focus; reserve its width so the row doesn't shift. Same link, title, target and rel as the header.
Update browser tests (link text in both places, hover-only on Pending) and screenshots; user-guide and CHANGELOG (no new version). Run the browser tests with pytest; report counts.
No branches, tags or commits.