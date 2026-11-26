0.60.1: window check regression and wording. Approved from your research.

1) Window check (CC-10/11/12): remove the skip of implementation tasks that fall inside a
   restricted period. Since 0.60.0 CC-05 reads only the change window, so every implementation
   task is checked against its allowed hours regardless of restricted periods.
2) calendar.yaml window_check task_exclude: add "validation", so a task whose name contains
   validation or certification is never an implementation task (exclude wins over include).
   Validation and certification tasks may run in any window and are not checked.
3) Wording:
   - CC-05 advisory: label "Check" instead of "Fix". In Scope = No: "'In scope of
     Restriction' is No. If the change is in scope, set it to Yes and complete the Restriction
     Exception Work Detail." Blank: "'In scope of Restriction' is not set. Set it, and if Yes
     complete the Restriction Exception Work Detail." Yes and complete: no fix line.
   - CC-12 fix text names all accepted window exception types (Windows Exception, Restriction
     Exception, Restriction Approval Notes), matching CC-10's How to meet it.
   - At a glance Freeze value "Marked not in scope of restriction" / "Scope not set" in
     neutral text colour (not orange).
4) Tests (made-up fixtures): implementation task inside a restricted period is checked
   (inside allowed hours -> pass; outside -> CC-10); "Implementation ... Validation" task
   excluded; validation/certification tasks never produce CC-10/CC-12; wording per case.
5) CHANGELOG 0.60.1, pyproject 0.60.1; docs where the skip or exclusions are described.

Verification: ruff; tests for changed modules; browser -k review and -k pending. Report rule
set old -> new and live CC-10/CC-12 counts before/after (codes and counts only); expected
CC-12 28 -> 10, CC-10 unchanged. Do not run --update-baseline or the audit. No git.
Do not read cr_core/config.py, cr_core/history/config.py or .env. Never delete anything under
work/history/. No heredocs (not even empty ones), python -c, python - or stdin redirects.
Delete work/cc12_review.md at the end.