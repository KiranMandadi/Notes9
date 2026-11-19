0.55.0 polish (baseline NOT updated). UI level (browser tests -k review only). No
heredocs, python -c or python - : any of them is a stop condition — ask instead.
1) Panel: remove the old rule facts rows (Severity, Status, Effect on score) below the
   new section; fold "Applies to" into "When it counts". Keep the rule's description
   sentence, How to meet it, source and catalogue link.
2) "What was checked": never repeat the panel title. Use the requirement plus why it
   matters (from the rule's description), e.g. GEN-01 "A deployment change names exactly
   what is deployed, so everyone can check what is deployed and what to roll back to."
   Apply to every rule; test that checked != title.
3) Plain wording, no internal terms ("pack", "first release", rule-set jargon):
   GEN-01 why: "Minor for now. It is planned to become Major after the platform review."
   CC-06 why: "For information only: no maximum window length has been agreed, so a long
   window does not change the score." Scan all explanation texts for "pack", "release of
   the", grammar slips; report any you changed.
Report rule set id. Then stop.

python scripts/check.py --update-baseline
python scripts/check.py --browser --audit
git status
git add -A
git status
git commit -m "0.55.0: 'How this was assessed' explanation for every finding" -m "- Each finding carries what was checked, what was found, why this severity, what would
  change it and when it counts, set by the rule that raised it
- 'How this was assessed' link on every issue and advisory, always visible; opens the
  rule panel with the explanation above How to meet it and the source
- Specific severity reasons for CV-15, CV-18, CC-05/06/09/10/12, CV-13, CV-14, MF-01,
  INF-05 and the Exec Summary rules; plain fixed-severity wording for the rest
- Change Assessment questions shown as chips (core bold, gaps amber)
- Same panel in the Pending overlay; Guide FAQ, user guide, CHANGELOG and tests updated
- Rule set 57e6af7f -> <new id>; baseline updated"
git push