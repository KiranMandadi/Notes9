Cleanup inventory (read-only). No code, config, doc or test changes in this step.
Constraints: never read/search/print cr_core/config.py, cr_core/history/config.py or .env;
no Remedy writes; no crq login; no git; no inline Python — scripts in a file under work/,
deleted after; chat shows codes, counts and file paths only — no change numbers or names.

Goal: find leftovers from 0.48–0.52.1 so the repo is clean, accurate and consistent,
WITHOUT changing any behaviour. List candidates only.

1) Dead or obsolete code: functions, classes, builtins, JS/CSS, templates, routes and
   flags no longer called or reachable — especially remnants of retired MF-05, CC-07,
   CC-08, the old calendar periods (mf-online, mf-batch-critical, business-hours, weekend
   max_risk), the CC-04 SCT text search, the rule "owner" field/row, the old loading pill,
   the old CC-06 Minor path. Show evidence (no callers / no references).
2) Config and rule packs: keys nobody reads, unused shapes/patterns (e.g.
   standard_template_number if truly unused), the unused rule-pack "question:" field,
   stale comments ("to be confirmed", "Change Management office"). Note which items would
   change the rule set id if touched (those are OUT of scope for cleanup).
3) Docs: every doc vs current behaviour — rule catalogue, user-guide, configuration,
   operations, architecture, contracts, SECURITY.md, open-items (D21/D24 etc.), README,
   .env.example, copilot-instructions, Guide page text. List statements that are wrong or
   outdated (retired rules still described, old thresholds like "8 h Minor", old counts,
   old versions, duplicated or contradictory sections, broken links/anchors).
4) Tests: obsolete or duplicated tests, misleading names (e.g. the "fallback" test names),
   skipped tests with no reason, fixtures nobody uses. Never propose weakening a test.
5) Code quality: unused imports/variables, commented-out code, TODOs that are done,
   inconsistent naming, ruff/lint warnings currently suppressed without reason.
6) Repo hygiene: stray files (work/ leftovers, scratch scripts, old outputs), .gitignore
   gaps, files that should never be committed.

For each candidate: id, file(s), what, evidence, proposed action (delete / rewrite doc /
rename / leave), risk (none / low / changes behaviour), and whether it would change the
rule set id. Anything that changes behaviour or the rule set id goes in a separate
"NOT cleanup — needs a decision" list.
Write the full list to work/cleanup_inventory.md; in chat give counts per section and the
"needs a decision" list. Then stop.