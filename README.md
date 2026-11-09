Evidence highlighting for text-field findings. Same standing rules from .github/copilot-instructions.md (including Running commands); no git operations unless I ask. If you ask me something and get no answer, stop and wait. UI only: no rule pack or scoring change; the rule set id must stay 567de08d — confirm it at the end.

1. Finding evidence snippet: for any finding whose evidence is a match inside a text field (Notes, Backout plan, Summary, Details, Deployment strategy, Work Details, etc.), show the surrounding text instead of only the matched words:
   - About 120 characters around the match, trimmed at word boundaries, "…" where cut, line breaks shown as spaces.
   - The matched text in bold. Field name stays as the underlined link before it ("Notes: …").
   - Use the exact match position the rule recorded; if the rule doesn't record one today, add it to the finding data (start/end offsets) without changing when or how the rule fires.

2. Highlight in Full change details: in the field's full text, wrap every matched span for that finding in a highlight (background #FDF0DC, bold, 2 px radius, no other change to the text).
   - Clicking the field link in the finding expands the field if collapsed, scrolls to the first highlight, and pulses it once (background fades from #F8D9A8, about 1 s).
   - When a finding has more than one match in the field, show a small "1 of N ‹ ›" stepper at the top-right of that field's box to move between them.
   - Highlights from different findings in the same field are all shown; hovering one shows the finding's rule code in a tooltip.

3. Same behaviour in the report page, the Pending overlay and the Executive brief where evidence appears. Escape all text safely (no HTML injection from Remedy content).

Tests:
   - snippet trimming and bold match;
   - offsets recorded for text-match findings;
   - highlight present on the exact span;
   - link click expands, scrolls and pulses;
   - stepper with 2+ matches;
   - text containing < > & renders as text.
Run python scripts/check.py --browser --audit: expect 0 mismatches and the same rule set id (567de08d). Update screenshots, user-guide; CHANGELOG (no new version). Run all tests with pytest; report counts.
No branches, tags or commits.


git status
git add -A
git commit -m "Evidence highlighting: context snippet in findings, highlighted match in change details"
git push