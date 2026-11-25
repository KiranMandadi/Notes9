0.59.0: retire MF-01 and GEN-01.

Remove two rules completely, by decision after user feedback:
- MF-01 "The LPAR, region or subsystem affected is named" (mainframe pack)
- GEN-01 "The change names the release (version, build, artifact or image tag)"

1) Rule packs: delete both rule entries; bump each affected pack's version. If the mainframe
   pack is left with no rules, keep the pack file and its classification but say so in the
   report (do not delete classification.yaml entries; the Platforms row still uses them).
2) Code: remove any check function, helpers, config keys, phrase lists and explain/"How this
   was assessed" texts used only by these two rules. Do not touch shared helpers used by
   other rules; list any helper you kept because something else uses it.
3) Headline/summary: the "name the LPAR, region or subsystem" and "name the release …"
   fragments disappear with the findings; check no leftover wording, fix text, Guide, Rules
   page entry or catalogue entry still mentions them.
4) History and old reports: findings already stored for these rule IDs must still display
   (or be ignored) without errors; do not delete or rewrite anything under work/history/.
5) Tests: delete tests that exist only for these rules; update any test that counts rules,
   asserts a headline, or uses them as examples. Add one test that neither rule ID appears
   in the loaded rule set.
6) Docs: rules catalogue, user guide, configuration and authoring docs; CHANGELOG 0.59.0
   (one line each: retired after user feedback); pyproject 0.59.0.

Verification: ruff; tests for the changed modules; browser -k review and -k pending.
Report: files changed, packs and new versions, old -> new rule set ID, and on live data the
number of changes whose score changes (codes and counts only).
Do not run --update-baseline or the audit. No git. Do not read cr_core/config.py,
cr_core/history/config.py or .env. Never delete anything under work/history/.
Any heredoc, python -c or python - is a stop condition.


git add -A
git status
git commit -m "0.59.0: retire MF-01 and GEN-01" -m "- MF-01 (LPAR, region or subsystem named) removed after user feedback
- GEN-01 (release version, build, artifact or image tag named) removed after user feedback
- Headline, Guide, rules catalogue, docs and tests updated; stored history unaffected
- Rule set <old> -> <new>; baseline, CHANGELOG and tests updated"
git push