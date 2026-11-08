Pending polish. Same standing rules (including Running commands); no git operations unless I ask. Do not print group or organisation names.

1. View by spacing: 24 px between the All tile's right edge and the tray (match the mock-up "Pending - View by options", Tray + pointer). The pointer stays attached to the All tile's right edge, vertically centred, inside that gap; tray, tile sizes and colours unchanged.

2. Group popover hierarchy:
   - Organisation headings stay flush left, in line with "All groups".
   - Group rows (checkbox, name, count) are indented 20 px under their heading.
   - 12 px space above each organisation heading except the first.
   - No lines or dividers added.
   - Same indentation when searching and when "Show N groups with no changes" is expanded.

3. Group list height: if the list scrolls inside the popover, let the scrolling area grow to about 60% of the viewport height before it scrolls. Show a soft fade at the bottom edge while more content is hidden (none at the end). The search box stays fixed at the top; "Show N groups with no changes" and Done stay fixed at the bottom, outside the scrolling area. Apply the same height rule to the Organisation popover if it ever scrolls.

Check at 1440 and 1920 px with all approvers (9 organisations).
Update the browser tests for:
   - the tile-to-tray gap (24 px ± 2);
   - group row indent (20 px relative to its heading);
   - all headings with changes visible without scrolling at 1920 px;
   - search, "Show N groups" link and Done outside the scroll area.
Update screenshots; CHANGELOG (no new version). Run the browser tests with pytest; report counts.
No branches, tags or commits.

git status
git add -A
git commit -m "Pending: View by tile spacing, Group popover hierarchy and taller list"
git push