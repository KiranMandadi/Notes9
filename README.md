Pending polish. Same standing rules (including Running commands); no git operations unless I ask.
1. Filter card: add a 1 px #EEF1F6 horizontal rule between the FILTERS row and the VIEW BY row, spanning the full inner width of the card, with equal spacing above and below (match the current gap). No other lines added.
2. Quality column: centre the score and the status pill horizontally as one stacked unit; centre the QUALITY header (sort icon included). Keep the cell top-aligned so the score stays on the row's first line.
3. Report column: centre the Open button horizontally and vertically within the row (align-self: center); centre the REPORT header. All other cells stay top-aligned.
Check with 1-line and 2-line summaries at 1440 and 1920 px. Update the browser tests and screenshots; CHANGELOG (no new version). Run the browser tests with pytest; report counts.
No branches, tags or commits.

git status
git add -A
git commit -m "Pending: divider between Filters and View by, centred Quality and Report columns"
git push