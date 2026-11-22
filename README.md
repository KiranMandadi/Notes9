0.57.1: High awareness pill in soft yellow.

Change the "High awareness" colours everywhere they appear (Pending Window pill, phone
card copy, Review At a glance pill, Calendar day tint, any legend or tooltip swatch):
  text #6E5A12 on #FBF6E0, font-weight 400 (regular)
Keep the warning-triangle icon, size, radius, padding, height and spacing unchanged.
Freeze (#A61B1B on #FDE8E7, lock, bold), Critical awareness (#8A4B08 on #FDF0DC, bold),
Freeze · exception (grey) and Today/Tomorrow are unchanged.
If the colours are defined once as CSS variables, change them there; do not duplicate
hex values. No change to logic, precedence, tooltips, rules, scores or calendar.yaml.

Docs: update any place that describes the High colour (user guide, configuration.md).
CHANGELOG: 0.57.1 entry. pyproject version 0.57.1.
Tests: update any test that asserts the High colours or weight.
Verification: ruff; tests for the changed modules; browser -k pending and -k review.
Report the files changed and whether the rule set ID moved (it should not).
Ground rules as before; any heredoc, python -c or python - is a stop condition.
No git operations.


git add -A
git status
git commit -m "0.57.1: High awareness pill in soft yellow" -m "- High awareness: soft yellow (#6E5A12 on #FBF6E0), regular weight, on Pending, Review
  At a glance and Calendar; completes the warm scale Freeze > Critical > High
- Freeze, Critical, Freeze · exception and Today/Tomorrow unchanged
- No rule, score or rule set change; docs, CHANGELOG and tests updated"
git push