Docs-only edit; no code changes, no tests, no git operations unless I ask.
Add this section to .github/copilot-instructions.md, after the existing "Running commands" section, exactly as written. Do not change any other section. Then show me the final file's section list (headings only).

## Speed and testing
- Tiered checks — pick the lightest tier that fits the task:
  - UI or text only: run ruff, unit tests for the modules you touched, and only the browser tests for the areas touched (pytest tests/test_browser.py -k <area>). Do NOT run the accuracy audit or the full browser suite.
  - Rules, scoring, Remedy queries, history, server, security or data: run python scripts/check.py --browser --audit and all tests.
  - "Full gate" (check.py --browser --audit + all tests + screenshots + docs pass) only when I say "full gate". I do this once before committing a batch for the VM.
- Known failures: the search-placeholder fit at 390 px (since Chrome 157) is known. Report it in one line; don't investigate it unless asked.
- Docs and screenshots: don't regenerate screenshots or rewrite docs on every task. Add a one-line CHANGELOG entry only; I'll ask for a docs pass per batch.
- Decisions: decide small, reversible details yourself (spacing, wording within the spec, test names, internal naming) and list them under "Decided" in your summary. Stop and ask only for: scoring or rule behaviour, data or Remedy queries, security, deleting code or files, setting changes, or anything git.
- Measurements and one-off helper scripts: only when the task asks for them.
- Summaries: short — what changed (one line per item), "Decided" list, test counts, and anything I must do.


git add .github/copilot-instructions.md
git commit -m "Copilot instructions: tiered testing and faster task flow"
git push