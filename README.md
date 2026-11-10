Pending multi-select filters redesign (mock-up "Pending - multi-select filters (proposed)"). Same standing rules from .github/copilot-instructions.md (including Running commands); no git operations unless I ask. If you ask me something and get no answer, stop and wait. UI only: the rule set id must stay 983cafa1 — confirm it at the end.

Apply to every multi-select popover: Class, Status, Organisation, Group, Approver.

1. Remove the "All …" checkbox row. Instead, header links on the right of the popover title (12 px, 600, #0E7C74, underlined): "Select all" and "Clear"; Class also gets "Default" (back to All except Standard); Status gets "Default" (back to Scheduled For Approval).
   - Select all / Clear act only on values that have changes and are in scope.

2. "Only" link on every value row (and every Group organisation heading), shown on row hover and keyboard focus, right before the count: picks just that value in one click.

3. Values with 0 changes:
   - never ticked, never counted in the selection or the button label;
   - listed under a "Show N with no changes" link at the bottom (as Group does today); when shown, greyed (#8592A8) with an empty, disabled box;
   - Status stages not yet loaded on demand keep "Loads when selected" and stay enabled.
   - If a value the user ticked later drops to 0, it stays ticked and removable.

4. Button label (counting only values that have changes): "All" when everything with changes is ticked; "All except Standard" / "Scheduled For Approval" for the defaults; the value's name when one is ticked (full text, no ellipsis; Group/Organisation names without the "CES - " prefix only if the full name doesn't fit at 1440 px); "N selected" for several; active (teal) style whenever it differs from the default.

5. Nothing ticked: footer note "Pick at least one <filter>." in #A61B1B and Done disabled; closing the popover by Esc or clicking outside restores the previous selection. Otherwise the footer note shows "N of M selected" (Class keeps "Standard changes are not included by default." when Standard is unticked).

6. Group scoped by Organisation:
   - List only groups of the selected organisations, under each organisation's heading, in support_groups.yaml order; a line under the search: "Showing groups in all organisations" / "Showing groups in N selected organisation(s)".
   - Each heading has a tri-state box (ticked / – partly / empty) that ticks or unticks all its groups, plus "Only" and its count. Headings stay sticky while scrolling; groups indented 20 px.
   - Unticking an organisation removes its groups from the list and from the Group selection (keep the existing note).
   - Search, "Show N groups with no changes", fitted height and Done behaviour unchanged.

7. URL encoding unchanged (no parameter for defaults; comma lists otherwise). Approver and search text never in the URL.

Check at 1440 and 1920 px with all approvers.
Tests:
   - Select all / Clear / Default per filter;
   - Only on a value and on an organisation heading;
   - zero-count values hidden, not counted, not tickable;
   - button labels (All, default, single name, N selected);
   - nothing ticked disables Done and Esc restores;
   - Group scoping, heading tri-state, unticking an organisation drops its groups.
Update screenshots, user-guide (filters); CHANGELOG (no new version). Run all tests with pytest; report counts and the rule set id.
No branches, tags or commits.

git status
git add -A
git commit -m "Pending filters: Select all/Clear/Only, zero-count values tucked away, honest labels, Group scoped by Organisation"
git push