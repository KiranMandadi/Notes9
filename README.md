0.63.0: rule feedback batch. MF-02 Minor, inline Change Assessment answers, long window as
context.

1) MF-02 (batch change gives its jobs, scheduler and cycle): Major (-20) -> Minor (-5) for
   every MF-02 finding (jobs, scheduler and cycle alike). Logic, triggers, messages, fix
   text and lifecycle unchanged. "How this was assessed": "Why Minor: the detail helps the
   approver place the change in the batch schedule; its absence alone does not show the
   change is risky." Bump the mainframe pack version.
   Report only (no change): does MF-02 produce one finding per change or one per missing
   item, and the live count of changes with 1, 2 or 3 MF-02 findings.

2) Change Assessment answers written on the heading line: when a question heading line has
   text after the question's wording, with or without a colon, dash or "=", treat that text
   as the answer (e.g. "5. User Restoration ETA < 15 mins", "3.Roll Back Standard changeman
   backout"). If nothing follows on that line, read the following lines as today. Applies
   to every question; the attestation answer is still never quoted or stored.
   Also read "< 15 mins", "<15 min", "under 15 minutes", "within 15 mins" as at most
   15 minutes for CV-17/CV-18.

3) CC-06 ("A long window gives its reason"): retire it (status: retired; id reserved,
   history still shows its title). Keep the change-window reading it uses (used elsewhere);
   remove only what CC-06 alone uses. At a glance -> Schedule: add a "Window" row
   "<start> → <end> · <duration>"; when over 8 h, add a neutral tinted pill
   "Longer than 8 h" (same style as the grey Freeze pills, no icon). Exactly 8 h -> no
   pill. Saved reports show the same.

4) No other rule, score or UI change.

5) Tests: MF-02 findings are Minor (-5); inline answer with and without colon; heading-only
   line followed by the answer; "< 15 mins" -> 15-minute band (no CV-18); CC-06 never
   fires; window row with and without the pill. Update any test or fixture asserting the
   old MF-02 severity or CC-06.
6) Docs (rules catalogue, user guide), CHANGELOG 0.63.0, pyproject 0.63.0.

Verification: ruff; crq rules validate; tests for changed modules plus test_security;
browser -k review and -k pending. Report: old -> new rule set ID; live counts (all pages,
codes and counts only) before -> after for MF-02 points, CV-15 findings, CC-06 findings;
score changes; verdict changes (Blocked / Needs work / Ready).
No git, no baseline, no audit. Do not read cr_core/config.py, cr_core/history/config.py or
.env. Never delete anything under work/history/. No heredocs (not even empty ones),
python -c, python - or stdin redirects. Delete temp files in work/.


git add -A
git status
git commit -m "0.63.0: rule feedback batch" -m "- MF-02 (batch jobs, scheduler and cycle) Major -> Minor: a missing detail is a documentation
  gap, not proven risk
- Change Assessment answers written on the question's heading line are read (e.g. 'User
  Restoration ETA < 15 mins'); '< 15 mins' counts as up to 15 minutes
- CC-06 retired: a window over 8 h shows in At a glance ('Longer than 8 h') instead of asking
  for a reason
- Rule set <old> -> <new>; baseline, docs, CHANGELOG and tests updated"
git push