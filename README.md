Add to .github/copilot-instructions.md a "Verification levels" section, then stop (no
other changes, no test runs beyond ruff on nothing):

Verification levels — use the lowest level that covers the change unless the prompt says
otherwise:
- Quick (default): ruff; pytest only for the test files covering the changed modules
  (use -k to narrow). No browser tests, no audit, no live measurement.
- UI: Quick + only the browser tests for the affected page/component (-k guide, -k
  pending, -k review, ...). Never the full browser suite.
- Release: run only when the prompt says "release check". Full pytest, full browser
  suite, check.py --browser --audit. Kiran normally runs this himself before committing.
- Live measurement only when rule logic changes or the prompt asks for it; never for
  wording, display or docs changes.
- Report which level ran and the counts.