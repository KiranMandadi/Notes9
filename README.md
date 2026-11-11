Pending filter fixes. Same standing rules from .github/copilot-instructions.md; no git operations unless I ask. If you ask me something and get no answer, stop and wait. UI/filter logic only; rule set id unchanged — confirm it.

1. ORR and Risk Level defaults (my approvals view) are fixed selections, independent of counts:
   - ORR default = 4 – Very High + 3 – High ticked even when either has 0 changes. Risk Level default = Risk Level 5, 4, 3 ticked even when any has 0 changes.
   - These two filters always list every value in fixed order (ORR: 4 – Very High, 3 – High, 2 – Medium, 1 – Low, Not assessed; Risk Level: 5, 4, 3, 2, 1). Zero-count values stay in place with a greyed "0" count, still tickable; no "Show/Hide … with no changes" link for these two.
   - Labels for these two never collapse to "All" unless every value is ticked: default reads "ORR 4 – Very High, 3 – High" and "Risk Level 5, 4, 3".
   - All approvers view: both default to every value ticked ("All"). Other filters keep current behaviour.

2. Hidden-changes pill moves into the table's results row, right after "Showing N of M": "Sorted by ORR, then risk, then start time · Showing N of M · [K hidden by … · Show all M]". Pill shown only when K > 0; same colours. Remove the separate line above the table entirely; move "Review decisions · Decided N of M · Copy Decisions" into the same results row, before the search box. No duplicate "Showing" text anywhere.

3. Header link in all-approvers view: replace "Show my approvals" with "Show only <configured approver display name>" (e.g. "Show only Srinivas Sasapu"). If no default approver is configured, hide the link.

4. Approver text box: show a small "×" clear button inside the box on the right, only when it contains text (hover darkens it; tooltip "Clear"; keyboard-focusable; aria-label "Clear approver"). Clicking it empties the text, keeps focus in the box, and applies the all-approvers view and its defaults (same as removing the approver today). Esc inside the box does the same. Keep the existing × on the Approver chip working as today.

5. Phone: the results row wraps (pill on its own line, decisions and search below).

Tests (UI tier): defaults with 0-count values stay ticked and labelled; fixed value order; label never "All" for a partial selection; pill inside the results row and the old line gone; decisions in the results row; "Show only <name>" link and hidden when no default approver; Approver clear button hidden when empty, shown with text, clears and switches to all approvers, Esc does the same. Run ruff, touched unit tests and browser tests -k "pending or filter". List decisions under "Decided"; one CHANGELOG line.
No branches, tags or commits.


git status
git add -A
git commit -m "Pending: View by replaced by Risk filters; fixed ORR/Risk Level defaults; pill in results row; Show only <name>; approver clear button"
git push