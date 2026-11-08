Pending UI round. Same standing rules (including Running commands); no git operations unless I ask. Do not print group or organisation names in your replies.

1. Status filter label: show the full label, no truncation: "Status Scheduled For Approval" (default) or the single stage name. 2–3 stages ticked: "Status 2 stages" / "Status 3 stages"; all four: "Status All stages". No ellipsis on ANY filter button at desktop widths (Class, Status, Date, Organisation, Group, Approver); the filter row may wrap to a second line. Phone unchanged.

2. Organisation filter → multi-select (same component and look as Class/Status/Group):
   - Checkboxes; "All organisations" at the top, indeterminate (–) when only some are ticked.
   - Count per organisation; zero-count disabled, but a ticked value stays removable.
   - Button text: "Organisation All", the organisation name when one is ticked, "Organisation N selected" for several.
   - URL: comma list (same encoding style as Group); none for All. Approver and search text still never go in the URL.

3. Group filter organised by organisation:
   - Groups listed under small organisation headings (11 px caps, #5B6880, with count), in support_groups.yaml order.
   - Only the selected organisations are shown, or all when Organisation is All.
   - "Find a group" searches across what is shown; headings stay; a heading with no matching groups is hidden.
   - "Show N groups with no changes" stays as one link at the bottom.
   - Unticking an organisation also unticks its groups.
   - Button text follows the Organisation rules ("Group All" / name / "Group N selected").

4. Group popover label "All coordinator groups" → "All groups" (the filter matches Manager Group; see D37).

5. Organisation and Group popovers about 440 px wide; long names wrap to a second line, never an ellipsis. Same for Class and Status if any value is long.

6. Every multi-select behaves the same: changes apply immediately; a "Done" button and clicking outside both close the popover; Esc closes too.

7. Headline and sticky header when no approver is set: "All approvers · N changes" (sticky: "All approvers · N changes · <dimension>: <value> · N shown"). Remove all "your groups" wording: headline, sticky header, empty state ("No changes pending approval" plus the filter hint), and docs/user-guide.md (describe the scope as "the configured support groups").

8. View by panel (mock-up "Pending - View by options", Split hint "Tray + pointer"):
   - The value cards sit together in a tray: background #E3E8F0, 8 px padding, 12 px radius, 10 px gap between cards, inside the existing #F1F4F8 panel.
   - The All tile stays outside the tray on the left; a small triangle (11 px, pointing right) on the All tile's right edge, vertically centred, points into the tray. Triangle colour matches the tile: #0B1B33 when All is active, #FFFFFF when a value is selected.
   - Remove the old vertical divider. Keep "Grouped by <dimension>" on the tab row. Folder tabs, tile sizes and three-line cards unchanged.
   - Phone: no tray or triangle; tiles wrap two per row as today.

Check at 1440 and 1920 px with all approvers (9 organisations, 139 groups) and with the default approver.
Docs: user-guide (filters, headline), CHANGELOG (no new version).
Tests: browser tests for:
   - Status button text (default, one stage, 2 stages, all);
   - no ellipsis on filter buttons;
   - Organisation multi-select, counts and URL round-trip;
   - Group headings and organisation scoping, search keeping headings, unticking an organisation clearing its groups;
   - "All groups" label;
   - Done / outside click / Esc;
   - "All approvers · N changes" headline and sticky header;
   - View by tray present and triangle colour in both states.
Update screenshots. Run all tests with pytest; report counts.
No branches, tags or commits.

git status
git add -A
git commit -m "Pending: multi-select Organisation, Group by organisation, full filter labels, All approvers headline, View by tray"
git push