Overlay: move Review Decision into the toolbar. Same standing rules (including Running commands); no git operations unless I ask.
1. Overlay toolbar layout:
   - Left: Back to Pending (Esc), ‹ n of N ›, Next: <7 digits> (unchanged).
   - Right: the Review Decision group, then the close (×) button.
   - Remove "Review decisions · Decided N of M" and its progress bar from the overlay toolbar (Pending's decisions bar is unchanged).
2. Move the whole Review Decision group (accent bar, "REVIEW DECISION" title + status line, Approve and Needs work buttons) from the tab row into the toolbar, keeping its current styles, behaviour, hover/selected states and the A/N keys. It still appears only after the report has fully loaded, and is hidden while loading or on failure.
3. The tab row (Quality report · Executive brief) is no longer pinned; it scrolls with the report. The toolbar stays fixed at the top of the overlay.
4. Accent bar colour: Not decided #8592A8 (neutral grey); Approved #1E6B45; Needs work #B26A00. Status text unchanged.
5. Keep the toolbar a single row at 1440 and 1920 px; if space is tight, shorten "Next: <7 digits>" before anything else.
Update the browser tests (decision group in the toolbar, not in the tab row; no progress bar in the overlay; tab row not pinned; grey accent when undecided) and screenshots; CHANGELOG (no new version). Run the browser tests with pytest; report counts.
No branches, tags or commits.

git status
git add -A
git commit -m "Overlay: Review Decision in the toolbar, neutral undecided accent"
git push