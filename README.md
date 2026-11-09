Pending calendar redesign (mock-up "Pending calendar - current vs proposed", Proposed). Same standing rules from .github/copilot-instructions.md (including Running commands); no git operations unless I ask. If you ask me something and get no answer, stop and wait. UI only: the rule set id must stay 983cafa1 — confirm it at the end.

1. Bars:
   - Tinted background with a 3 px left edge in the status colour, matching the status pills: Blocked #FDE8E7 / edge #B42318 / text #7A1212; Needs work #FDF0DC / #C27A12 / #6B3A06; Ready #E3F4EA / #2F8A5B / #14532D.
   - 24 px tall, 5 px radius, 5 px gap between rows. Text: change number only (7 digits, IBM Plex Mono 12 px, 600).
   - Hover: shadow 0 2px 8px rgba(11,27,51,0.22) and a tooltip "<7 digits> · <start> → <end> · <status>[ · Freeze exception]".
   - Freeze exception: a small "❄" after the number instead of the yellow outline. Keep the "▸" marker when a bar continues into next week.

2. Click a bar to open the Quality report overlay for that change (same as Open in the list, with ‹ › stepping through the calendar's changes in display order).

3. Per day: show the first 8 rows; when a day has more, show a link in row 9 of that day: "+N more" (teal #0E7C74, underlined), followed by " · M Blocked" in #B42318 when M hidden changes are Blocked. Clicking expands the whole week; a "Show fewer" link collapses it. Multi-day bars count toward the day they start.

4. Order within a day: by start time (as today). Lanes stay packed so multi-day bars don't overlap.

5. Legend moves to the header row next to "N changes this week", with counts: "Blocked N · Needs work N · Ready N · ❄ Freeze exception". Remove the bottom legend.

6. Unchanged: week navigation, restricted-period banner, today's column outline, search, filters and View by applying to the calendar.

Check at 1440 and 1920 px with a busy week (30+ changes on one day) and a quiet week.
Tests:
   - bar colours and edge per status;
   - tooltip text;
   - ❄ marker;
   - bar click opening the overlay;
   - 8-row cap with "+N more · M Blocked";
   - expand and collapse;
   - legend counts.
Update screenshots, user-guide; CHANGELOG (no new version). Run all tests with pytest; report counts and the rule set id.
No branches, tags or commits.

git status
git add -A
git commit -m "Pending calendar: tinted compact bars, 8 per day with +N more, legend with counts, bars open the report"
git push