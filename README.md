Overlay: Review Decision in the tab row. Same standing rules (including Running commands); no git operations unless I ask. Mock-up: "Overlay - Review Decision options", option A.

1. Show the Review Decision controls only after the report has fully loaded (score and findings rendered). Hidden while "Reading … from Remedy…" and if the load fails.

2. Layout, right-aligned in the tab row (no box, no background):
   - A 4 px × 36 px vertical accent bar (2 px radius): teal #0E7C74 when undecided, green #1E6B45 when Approved, amber #B26A00 when Needs work.
   - Next to it: title "REVIEW DECISION" (11 px, 700, caps, letter-spacing 0.7px, #0B1B33) over a status line (12 px, #5B6880): "Not decided yet" / "Recorded: Approved" / "Recorded: Needs work".
   - Then the two buttons, 12 px gap.

3. Buttons "✓ Approve" and "↻ Needs work":
   - Size: 38 px tall, 16 px side padding, 14 px semibold, 8 px radius, 1.5 px border, shadow 0 1px 2px rgba(11,27,51,0.14).
   - Unselected: white; Approve text #1E6B45, border #7CC4A0; Needs work text #8A4B08, border #E8B266.
   - Hover (unselected): background #E3F4EA / #FDF0DC, shadow 0 2px 6px rgba(11,27,51,0.18), pointer cursor.
   - Pressed: translateY(1px). Focus-visible: 2 px #0E7C74 outline, 2 px offset.
   - Selected: solid fill (#1E6B45 / #B26A00), white text and border to match. Clicking the selected one again clears the decision.
   - No keyboard hints anywhere; the A and N keys keep working as before.

4. Pin the tab row (Quality report · Executive brief · Review Decision) directly below the overlay toolbar while the report scrolls. It is part of the layout and never covers content.

5. Overlay toolbar, right side: "Review decisions · Decided N of M" with a 120 × 6 px progress bar (track #E6EBF2, fill #0E7C74). Same N and M as the Pending decisions bar; updates immediately on a decision.

6. Unchanged: decisions are kept in sessionStorage for this tab only; never sent to the server, logged or put in the URL. Copy Decisions and the leave-page warning behave as today.

Check at 1440 and 1920 px.
Tests: browser tests for:
   - controls hidden while loading and on load failure;
   - accent colour and status text in all three states;
   - selected fill and click-again to clear;
   - hover style applied;
   - tab row pinned after scrolling;
   - toolbar progress matching Pending and updating;
   - A/N keys still working.
Update screenshots; CHANGELOG (no new version). Run the browser tests with pytest; report counts.
No branches, tags or commits.

git status
git add -A
git commit -m "Overlay: Review Decision after load, accent bar and clearer buttons, pinned tab row, decision progress"
git push