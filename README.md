0.62.0: retire CC-12 (window could not be confirmed).

Decision after user feedback: when no implementation task is recognised, the window check
says nothing. Some changes intentionally have no implementation task; the fallback to the
change window only produced noise.

1) Retire CC-12 with status: retired (like CV-02/03/08, MF-01, GEN-01): id reserved, stored
   history still shows its title. Bump the change-class pack version.
2) Remove the fallback that compares the change window when no usable implementation task
   exists, and any code, config keys, messages and "How this was assessed" text used only
   by CC-12. Keep everything CC-10 and CC-11 use; list any helper kept because they use it.
3) No change to CC-10 (implementation task outside its window, Major), CC-11, how
   implementation tasks are recognised, the exception types, or any other rule.
4) Tests: remove CC-12-only tests; add one that a change with only certification tasks
   (or tasks without times) gets no window finding; CC-10 tests unchanged and passing.
5) Docs (rules catalogue, user guide window section), CHANGELOG 0.62.0, pyproject 0.62.0.

Verification: ruff; crq rules validate; tests for changed modules plus test_security;
browser -k review. Report old -> new rule set ID and live counts (all pages, codes and
counts only): CC-12 before -> after (expected -> 0), CC-10 before -> after (expected
unchanged), verdict changes (expected none).
No git, no baseline, no audit. Do not read cr_core/config.py, cr_core/history/config.py or
.env. Never delete anything under work/history/. No heredocs (not even empty ones),
python -c, python - or stdin redirects. Delete temp files in work/.


git add -A
git status
git commit -m "0.62.0: retire CC-12 (window could not be confirmed)" -m "- No window finding when no implementation task is recognised; some changes intentionally
  have none, and the change-window fallback only produced noise
- CC-12 kept with status retired (id reserved, history still shows its title)
- CC-10 and CC-11 unchanged; no verdict changes
- Rule set <old> -> <new>; baseline, docs, CHANGELOG and tests updated"
git push