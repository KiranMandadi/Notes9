At a glance: Risk Report group. Same standing rules (including Running commands); no git operations unless I ask. If you ask me something and get no answer, stop and wait; do not proceed on your own.

1. In At a glance (report page and overlay), add a "RISK REPORT" group above "RISK", same heading style as the other groups, no caption or subtext:
   - "Aggregate risk value": from Risk Level - Computed (301557300), shown as "N – <legend>" using Remedy's risk report legend: 1 Minimal, 2 Low, 3 Medium, 4 High, 5 Extreme (e.g. "4 – High"). "—" if empty.
   - "Application ORR": moved here from RISK, unchanged ("4 – Very High", bold as today).

2. RISK group:
   - "Risk level" stays "Risk Level N" (field 1000000180).
   - When it differs from the aggregate, add a second line under the value in amber (#8A4B08, 12 px): "Below aggregate (N)" when lower, "Above aggregate (N)" when higher. Nothing when equal or when either value is missing.
   - Impact, Urgency, Priority unchanged.

3. Executive brief decision box: show "Aggregate risk value" next to Risk level, with the same format and the same Below/Above line.

4. CV-03 finding text: "The aggregate risk value (Risk Level - Computed) is N" instead of "Risk Level - Computed is N". Text only: no change to severity, points or when it fires.

5. Correct docs/research/orr-rating.md: the aggregate is held in Risk Level - Computed (301557300); Risk Level (1000000180) is the change's own value and can differ (one example by change number only).

Run python scripts/check.py --browser --audit: expect 0 mismatches and the same rule set id; report both.
Tests:
   - aggregate shown with its legend word, and "—" when empty;
   - ORR now under RISK REPORT;
   - "Below aggregate (N)" when lower, "Above aggregate (N)" when higher, no line when equal or missing;
   - Executive brief shows the aggregate.
Update screenshots, user-guide (At a glance) and the rules catalogue (CV-03 wording); CHANGELOG (no new version). Run all tests with pytest; report counts.
No branches, tags or commits.


git status
git add -A
git commit -m "At a glance: Risk Report group with aggregate risk value and ORR; flag when Risk Level differs"
git push