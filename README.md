UI polish round. Same standing rules from .github/copilot-instructions.md (including Running commands); no git operations unless I ask. If you ask me something and get no answer, stop and wait. UI only: no rule pack change, so the rule set id must stay 3f368251; confirm it at the end.

1. At a glance (report page and overlay) and the Executive brief decision box:
   - Rename the label "Aggregate risk value" to "Aggregate risk" (it must fit on one line). Value format unchanged ("4 – High").
   - Risk level note on the same line as the value, after a " · " separator (#8592A8): "Risk Level 1 · Below aggregate risk (4)". Note text amber (#8A4B08), same font size as the value. Wording: "Below aggregate risk (N)" / "Above aggregate risk (N)". It may wrap under the value on narrow widths; no note when equal or when either value is missing.

2. Clear decisions dialog: make the Cancel button clearly a button: 1.5 px #CFD7E3 border and #F4F6FA background (hover #EEF1F6). "Clear decisions" unchanged.

Check at 1440 and 1920 px.
Tests:
   - "Aggregate risk" label on one line;
   - inline note text and colour for below, above, equal and missing;
   - Cancel button styles.
Update screenshots, user-guide; CHANGELOG (no new version). Run all tests with pytest; report counts and the rule set id.
No branches, tags or commits.


git commit -m "UI polish: Aggregate risk label, inline risk level note, clearer Cancel button"