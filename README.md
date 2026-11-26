0.60.2: Freeze pill wording and At a glance Freeze row. UI only; no rule, score or config change.

1) Pill labels (Pending Window column, phone card, tooltip header, At a glance):
   - "Freeze · not in scope"  ->  "Freeze · marked out of scope"
   - "Freeze · scope not set" and "Freeze · exception" unchanged
   - Red "Freeze" keeps the lock icon; the grey pills have no icon.
   Tooltip note for the marked case: "Marked out of scope of restriction by the change"
   (instead of "Marked not in scope of restriction").

2) At a glance -> Freeze row: show the same pill as Pending, with the overlapping restricted
   period(s) on the line below, one line per period:
     "<period name> · <Ddd d Mon HH:MM> – <Ddd d Mon HH:MM> ET"
   matching the Awareness row layout. For In Scope = Yes with a missing or incomplete
   exception add a line "No Restriction Exception recorded" / "Restriction Exception
   incomplete". No overlap: plain text "No restricted period".

3) Tests: browser test per case (marked out of scope, scope not set, exception complete,
   exception missing/incomplete, no overlap) for both Pending and At a glance; no remaining
   "not in scope" pill text anywhere (grep the static files and templates).
4) Docs: user guide wording for the pill; CHANGELOG 0.60.2; pyproject 0.60.2.

Verification: ruff; tests for changed modules; browser -k pending and -k review.
Confirm the rule set ID is unchanged. No git, no baseline, no audit.
Do not read cr_core/config.py, cr_core/history/config.py or .env. Never delete anything under
work/history/. No heredocs (not even empty ones), python -c, python - or stdin redirects.

git add -A
git status
git commit -m "0.60.2: clearer Freeze pill and At a glance Freeze row" -m "- 'Freeze · not in scope' renamed 'Freeze · marked out of scope' (a declaration, not a verdict)
- At a glance Freeze row shows the same pill as Pending with the restricted period and dates
- UI only; rule set unchanged"
git push