0.55.0: "How this was assessed" explanation for every finding. Constraints unchanged; no
git; never run python -c / python - / heredocs (scripts in a file under work/, deleted
after); do NOT run --update-baseline. Verification: UI level (ruff, tests for changed
modules, browser tests -k review only).
Design: board "Review - why this finding (explanation panel)".

1) Each finding carries an "assessment" block, set by the rule that raised it (report
   contract change): checked (the requirement, one sentence), found (this change's
   evidence; never names, submitter or Q7 attestation text), severity_reason (why this
   severity), would_change (what would make it more or less severe, or "This rule is
   <severity> for every change it applies to"), when (lifecycle, e.g. "Scored while
   awaiting approval; for information once Scheduled").
   Specific reasons for rules with variable severity: CV-15 (core vs supporting, gap
   count), CV-18 (customer harm + restoration band), CC-10/CC-12 (which condition made
   it advisory), CV-14 and Exec Summary rules (lifecycle), MF-01 (Please confirm vs
   Major), CC-05/CC-09 (freeze), CV-13 (stale tasks), CC-06 (advisory reasons). All other
   rules: fixed-severity wording. Text lives in rule packs/config; neutral wording.
2) Report: each issue ends with its own line "ⓘ How this was assessed" (muted teal link,
   below "Searched:"), always visible — not tied to Technical details; keyboard
   focusable; aria-label "How <rule id> was assessed". Same on advisories.
3) Click opens the existing rule side panel with a new top section: header "<rule id> ·
   <pack>"; label "How this was assessed" and a plain title; What was checked; What was
   found (for CV-15 the nine questions as chips — core bold, missing/unanswered amber,
   with a legend); a tinted box with severity badge, points, "Why Major/Minor/advisory",
   severity_reason and would_change; When it counts. Below, unchanged: How to meet it,
   source, "View in the rules catalogue". Rule id shown in the panel header regardless
   of Technical details. The selected issue row is highlighted while the panel is open;
   Esc closes it.
4) Pending overlay uses the same panel. Guide: FAQ line "How was this assessed?";
   user-guide paragraph; CHANGELOG 0.55.0; pyproject 0.55.0.
Tests: every finding in sample reports has a complete assessment block; CV-15 Minor and
Major reasons; CV-18 quotes the band; CC-12 explains advisory; fixed-severity wording;
no names or Q7 text in any block; link visible with Technical details off; panel opens/
closes by keyboard. Report rule set id, files and test counts. Then stop.

python scripts/check.py --update-baseline
python scripts/check.py --browser --audit
git status
git add -A
git status
git commit -m "0.55.0: 'How this was assessed' explanation for every finding" -m "- Each finding carries what was checked, what was found, why this severity, what would
  change it and when it counts, set by the rule that raised it
- 'How this was assessed' link on every issue and advisory, always visible; opens the
  rule panel with the explanation above How to meet it and the source
- Specific severity reasons for CV-15, CV-18, CC-05/09/10/12, CC-06, CV-13, CV-14,
  MF-01 and the Exec Summary rules; fixed-severity wording for the rest
- Change Assessment questions shown as chips (core bold, gaps amber)
- Same panel in the Pending overlay; Guide FAQ, user guide, CHANGELOG and tests updated
- Rule set <old id> -> <new id>; baseline updated"
git push