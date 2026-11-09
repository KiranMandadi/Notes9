Risk Level display: use Remedy's own value. Same standing rules (including Running commands); no git operations unless I ask.
1. Wherever a single change's risk is shown, display Remedy's value as "Risk Level N" (from field 1000000180, e.g. "Risk Level 3"), with no added word:
   - Pending table cell and phone line;
   - View by Risk Level cards (five cards: Risk Level 5 down to Risk Level 1) and their hover text;
   - report At a glance, overview box, Executive brief decision box;
   - finding text (CV-03 "Risk Level - Computed is 4"; X-04, Q-RISK-01, PCF-03 "Risk is rated Risk Level N");
   - CLI risk_shown.
   Remove the Critical/Minimal word map in pending.js and the "N (word)" builders (shown_level, risk_text, riskText).
2. Keep the internal three-band grouping (1–2 Low, 3 Medium, 4–5 High) and every rule, threshold and setting that uses it unchanged: no score, finding, severity or status may change.
3. Where output is counted or labelled by band (cli.py counts, render.py executive summary risk grid and "High risk" wording, schedule_view.py), name the levels covered: "High (Risk Level 4–5)", "Medium (Risk Level 3)", "Low (Risk Level 1–2)".
4. Sorting by risk uses the number, highest first (unchanged).
5. Do not change the create-change write mapping (remedy_field_map.yaml lines 208–211); add a note to docs/open-items.md that it only writes levels 2–4.
Run python scripts/check.py --browser --audit: expect 0 mismatches and the rule set id unchanged; report both. Update tests, screenshots, user-guide and rules catalogue wording; CHANGELOG (no new version). Run all tests with pytest; report counts.
No branches, tags or commits.